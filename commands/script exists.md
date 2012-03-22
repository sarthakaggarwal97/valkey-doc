Returns information about the existence of the scripts in the script cache.

This command accepts one or more SHA1 sums and returns a list of ones or zeros to signal if the scripts are already defined or not inside the script cache.
This can be useful before a pipelining operation to ensure that scripts are loaded (and if not, to load them using `SCRIPT LOAD`) so that the pipelining operation can be performed solely using `EVALSHA` instead of `EVAL` to save bandwidth.

Plase check the `EVAL` page for detailed information about how Redis Lua scripting works.

@return

@multi-bulk-reply
The command returns an array of integers that correspond to the specified SHA1 sum arguments. For every corresponding SHA1 sum of a script that actually exists in the script cache, an 1 is returned, otherwise 0 is returned.

@example

    @cli
    SCRIPT LOAD "return 1"
    SCRIPT EXISTS e0e1f9fabfc9d4800c877a703b823ac0578ff8db ffffffffffffffffffffffffffffffffffffffff