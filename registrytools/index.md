---
title: WMI Registry Tools for JScript
author: Matthew Smith
layout: page
---

Warning: this script provides functions that can modify the registry. As with any registry modification, the machine can be rendered non-functional by an improper edit. USE AT YOUR OWN RISK! I am not responsible for destroyed registries and unbootable computers!


**Description**: This JScript library\** provides several functions that allow scripts to interface with the [WMI Registry provider][1] on local or remote machines. The library is intended to be run on/against Windows machines through the [Windows Scripting Host][2]. This reduces redundant code and makes the WMI registry functions as simple to use as the WSH registry functions.

**Computer and Hive Arguments**

All functions require *computer* and *hive* arguments. *Computer* should be a string containing an IP address or computer host name of the computer you wish to operate upon. If you are working with the local machine, use &#8220;.&#8221; for the *computer* argument. *Hive* is a string that determines which root hive you wish to connect to. The options are listed below (ie if you wish to retrieve a key under HKEY\_CURRENT\_USER, you would pass HKCU to the function).

hive			argument
================================
HKEY_CLASSES_ROOT	HKCR
HKEY_CURRENT_USER	HKCU
HKEY_LOCAL_MACHINE	HKLM
HKEY_USERS		HKU
HKEY_CURRENT_CONFIG	HKCC
================================

**Functions**:

*   registryToolsEnumValues(computer, hive, key)
    
    *   This function gets a list of all the values under a given key in the registry and returns an array of values and associated data types.
    *   Takes three inputs: 
        *   *computer* &#8211; see above
        *   *hive* &#8211; see above
        *   *key* &#8211; a string containing the name of the key you wish to enumerate (list the values of)
    *   Returns an object containing two arrays: 
        *   *values* &#8211; an array containing the string names of each value
        *   *types* &#8211; an array containing a string denoting the data type of each value (REG\_SZ, REG\_BINARY, REG\_DWORD, REG\_EXPAND\_SZ, REG\_MULTI_SZ)
        *   these arrays are related by index (ie values[0]  types[0])
*   registryToolsReadValue(computer, hive, key, value, type)
    
    *   Reads the data in a given value in the registry
    *   Takes five inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; a string containing the name of the key containing the value you want to read
        *   *value* &#8211; the name of the value who&#8217;s data you want to read
        *   *type* &#8211; the data type of the value (can be found using *registryToolsReadValue* or looking in the registry). Should be one of the following strings: REG\_SZ, REG\_BINARY, REG\_DWORD, REG\_EXPAND\_SZ, REG\_MULTI_SZ
    *   Returns the data contained in the value. Data type depends on the type of the requested value, according to the following table: 
        type		returns
===========================
REG_BINARY	int
REG_DWORD	int
REG_EXPAND_SZ	string
REG_MULTI_SZ	string array
REG_SZ		string
===========================

*   registryToolsWriteValue(computer, hive, key, value, type, data)
    
    *   Writes the given data to the given registry key/value
    *   Takes six inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; the key containing the value you want to write to
        *   *value* &#8211; the name of the value who&#8217;s data you wish to set
        *   *type* &#8211; the type of data you wish to write: 
            type		input data type
==================================================
REG_BINARY	array of ints
REG_DWORD	hex or decimal number (int)
REG_EXPAND_SZ	string
REG_MULTI_SZ	array of strings
REG_SZ		string
==================================================
        
        *   *data* &#8211; this argument should contain the data you wish written into the value, in the type specified
    *   Outputs: 
        *   none (currently, later revisions may return an error code if applicable)
*   registryToolsDeleteValue(computer, hive, key, value)
    
    *   Removes the specified value from the given registry key
    *   Inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; string containing the key containing the value you wish to delete
        *   *value* &#8211; string containing the name of the value to be deleted
    *   Outputs: 
        *   none currently
*   registryToolsEnumKeys(computer, hive, key)
    
    *   Lists the sub-keys of the given key
    *   Inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; string containing the name of the key to be enumerated
    *   Outputs: 
        *   an array of strings containing the names of the sub-keys
*   registryToolsCreateKey(computer, hive, key)
    
    *   Creates a new key
    *   Inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; the name of the key to be created (you can use &#8220;key//subkey//subkey2&#8243; to nest keys)
    *   Outputs: 
        *   none for now
*   registryToolsDeleteKey(computer, hive, key)
    
    *   Removes given key (and all sub-values) from registry, but only if there are no sub-keys
    *   Inputs: 
        *   *computer, hive* &#8211; see above
        *   *key* &#8211; the name of the key to be removed
    *   Outputs: 
        *   none currently

**Note on &#8220;JS Library&#8221;**: Since WSH and JScript do not normally support the inclusion of external code into a script, a handy workaround is found various places on the internet. I don&#8217;t take credit for this code!

In the script that you wish to make calls from, you must have two things: the *include* function (only needed once), and an *eval* call (which you use for each external file you wish to include). You can place the *include()* function anywhere in your script, but be sure that your *eval* statement occurs before the first time that you try to call an external function.

**The Include() Function**  
function include(fileName) {  
var fso = new ActiveXObject(&#8220;Scripting.FileSystemObject&#8221;); // create the file system object  
if( !fso.FileExists(fileName) ) { return -1; } // check for file existance and fail if no file  
var file = fso.OpenTextFile(fileName);  
var stream = file.ReadAll();  
file.Close();  
return stream;  
}  

**The Eval() Call**  
eval( include(&#8220;wmiRegistryTools.js&#8221;) );  

**References**

I referred to the following pages while writing this script. There are probably even more pages that I found useful but who&#8217;s links I have forgotten.

*   [The MSDN Reference for StdRegProv][1]
*   [Script Man&#8217;s (Tom Medhurst) Page on WMI Software Installation][3] (hugely helpful in figuring out how to interact with StdRegProv using JScript!)

 [1]: http://msdn2.microsoft.com/en-us/library/aa393664(VS.85).aspx
 [2]: http://en.wikipedia.org/wiki/Windows_Script_Host
 [3]: http://jscriptman.blogspot.com/2006/03/installed-software-on-pc-via-wmi.html
