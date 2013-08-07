Hashtest
========

Validate integrity of in memory code using hashes

Made up of two components, Hashbuild and Hashtest.
For more details see paper @ http://dfrws.org/2013/proceedings/DFRWS2013-12.pdf

Hashbuild
---------
  Parses a mounted filesystem and creates a hash set for all Portable Executable (PE) files on the disk
  
  Usage
    python hashtest.py <mount point> <output file>
    
    
Hashtest
--------
  Takes a hash set and validates the code in user space memory for a given memory image
  Requires Volatility, tested on version 2.2
  Dumps pages that are not validated to a specified directory
  
  Usage
    python vol.py -f <memory image> --profile <memory image OS> hashtest -D <dump directory>
  
  Output categories
    Verified      - code hash matched stored hash
    Failed        - code hash did not match stored hash
    Unknown       - code hash information did not exist for page
    Unverifiable  - default Windows behaviour that cannot be verified (see paper)
  
  
Note: code is still a little messy, a cleaned up version is coming soon
