FileBytes
================

Scripts to parse the following file formats:
- Executable and Linkage Format (ELF),
- Portable Executable (PE) and
- MachO

Install
-------

Install FileBytes

    $ python setup.py install

Samples
-------

Parsing ELF file
```python
from filebytes.elf import *
elf_file = ELF('test-binaries/ls-x86')

elf_header = elf_file.elfHeader
sections = elf_file.sections
segments = elf_file.segments # elf_file.programHeaders does the same
```

Parsing PE file
```python
from filebytes.pe import *
pe_file = ELF('test-binaries/cmd-x86.exe')

image_dos_header = pe_file.imageDosHeader
image_nt_headers = pe_file.imageNtHeaders
sections = pe_file.sections
data_directory = pe_file.dataDirectory

import_directory = pe_file[ImageDirectoryEntry.IMPORT]
export_directory = pe_file[ImageDirectoryEntry.EXPORT]
```

Parsing MachO file
```python
from filebytes.mach_o import *
macho_file = MachO('test-binaries/ls-macho-x86_64')

mach_header = macho_file.machHeader
load_commands = macho_file.loadCommands
```

For further samples look at the sample folder.

Contributions
----------------------
If you would like contribute, here some ideas:
- Implementation of parsing of missing LoadCommand types for MachO files
- Implementation of parsing of the missing section types for ELF files
- Implementation of parsing of the missing data directory fields for PE files

But any kind of contribution is welcome. :)


Project page
------------------------------------
https://scoding.de/projects/