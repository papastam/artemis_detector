# Prerequisites
- Go 1.21+

# Compile
In order to compile the application you need to run the following command:
```bash
go build -o artemis_detector main.go utils.go
```

# Run
The application has two running modes:
- **detect_all**: In this mode the detector will detect hijacks for every AS possible.
- **detect_as**: In this mode the detector will detect hijacks for a specified AS, given to it using the __--asn 〈AS#〉__ flag

## Flags
- **--updates** \<File(.csv) | Dir\>: The BGP updates file/directory
- **--input_type** \<”file”|”directory”\>: The type of input you are providing the tool with _(default:”file”)_
- **--prefixes** 〈prefixes_file.txt〉: The file containing the legal prefixes of each AS.
- **--output** \<output_file(.csv)\>: The file where the detector will write the final detected hijacks
_(will be created if not exists)_
- **--asn**: The AS number to detect hijacks for. If not specified, the detector will run in detect_all mode.

## Output
The detector will print the analysis statistics in the output of the terminal. The output of the detection can be found in the file specified with the –output flag. This csv file will contain the
following information for each detected hijack:

- prefix
- origin as
- hijack type
- hijacker asn
- time started
- time of last update
- time ended
- state
- duration