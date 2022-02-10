# VFD SWMR Utilities

(maintained separately from the HDF5 library)

To support NFS file system, this utility applies the updater files to the copy of the metadata file. To check it out, go to the HDF5 directory and do the following two steps:
    1. git submodule init
    2. git submodule update

Usage: aux_process [options] <md_file> <ud_path>

Where: <md_file> is the path to the metadata file. Must be on a POSIX file system. Note that the file may not exist yet.
       <ud_path> is the path of the updater files including the directory. This will typically be in an NFS mounted file system.

Options:
    -a --skip_aux:       Exit if VDS across multiple file is being enabled (to be implented in the future).
    -c --vfd_config:     Quoted string containing the configuration string for the VFD stack to be used. Default: sec2
    -l --log_file:       Path to the log file. Default: no log file.
    -m --md_chksum_path: Path to the file containing the checksum values for testing purpose.
    -p --polls_per_tick: Number of times to poll for a new updater file per tick. Default: 10.
    -s --stats:          Display stats on exit.
    -t --tick_len:       Integer value indicating the tick length in tenths of a second.
    -v --verbose:        Write log entries to stdout.

### Making Changes

If you update this code, please update the appropriate VFD SWMR branch(es) in the main HDF5 repo:

0) Initialize
   * Clone the HDF5 repo and check out the appropriate branch
   * `` git submodule init ``
   * `` git submodule update ``
1) Switch to the `` utils/vfd_swmr `` directory
2) `` git pull origin main ``
3) Back up to the source root and run `` git diff ``. You should see the commit changed.
4) Create a branch, commit, push, make PR, etc.
