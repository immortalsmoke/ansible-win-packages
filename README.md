# ansible-win-packages
Installs a applications on a Windows server programs using binaries stored within this role.

##### Instructions
1. Put binaries for applications in `files/`
2. Define var `package_list`, a list of dicts.  For each list entry, you will need:
   - `path`: the filename of the binary
   - `product_id`: the [product ID](https://docs.microsoft.com/en-us/windows/desktop/msi/product-codes) of the software
   - `arguments`: installation arguments, e.g. silent install

#####  Task Overview
1. Creates temp dir `C:\Temp`
2. Copies a list of binaries defined in var package_list over to the target server
3. Installs list of packages using the args provided in package_list
   
##### Assumptions
1. var `package_list` is defined

##### Additional Notes
The "product_id" value required by win_package can be found in the Windows Registry.  I had to install the applications on my own system first to grab the ID from the registry.  There might be a better way to do this.

