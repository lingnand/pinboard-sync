pinboard-sync
=============

[pinboard-sync](https://pinboard.lynnard.tk) is a simple shell script that allows you to synchronize your [Pinboard](http://pinboard.in) bookmarks with your local cache.

By default, the local cache is stored at `~/.config/vimb/bookmark`, in the format of `<href>TAB<description>TAB<space delimited tags>`, which can be read natively by [vimb](https://github.com/fanglingsu/vimb/).

Whenever the script runs, it merges the newest changes from the cloud as well as the local copy, and propagate them to both locations to make sure your bookmarks are in sync. This thus allows you to seamlessly interface your browser with Pinboard with regard to bookmarks.

## Dependencies

* `curl`: for pulling and pushing data from/to the Pinboard cloud
* `diff`: for comparing local cache differences

## Configuration

* `~/.pinboard/config`: the default config file holding your pinboard account details
    * the first line is your username
    * the second line is your API token
    * alternatively, you can use `pinboard login` to log into your account
* `$BOOKMARK_FILE`: the location of the local cache
* other options are available inside the script

## Usage

    pinboard login|synchronize|help

* `login`: log into your account and generate the config file
* `synchronize`: synchronize your local cache with Pinboard cloud, update timestamp, and backup your local cache
* `help`: help messages

## Integration with crontab

Simply put the following line into your crontab file

    */5 * * * * pinboard synchronize

to run the script every 5 minutes for synchronization, for example.
