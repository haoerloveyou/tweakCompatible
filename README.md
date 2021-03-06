## Why was this made

Previously when a new jailbreak was released, the community manages a large google spreadsheet. The old process is super time consuming and tedious to cross reference against your device.

## What does it do

![Screenshot](docs/screenshot1.jpg?raw=true "Screenshot1")
![Screenshot](docs/screenshot2.jpg?raw=true "Screenshot2")

In the spirit of open source and to give back, I spent some time writing this tweak for Cydia that adds a search button to the right of the package details page. When clicked, it displays community driven compatibility info into an alert box.

Users can also go to the frontend website @ https://jlippold.github.io/tweakCompatible/ to view user submissions.

## Submissions

In order to submit whether a tweak works with an iOS version, you need to submit a review via Cydia. If you click the search button, then the `This Package Works!` button, you will be redirected to github issues with a pre-populated issue created. A github account is required to submit reviews.

Every hour, I pull any open issues, update `docs/tweaks.json`, and close the ticket. This is done by cron.

## Scripting

This repo also contains a nodejs script, `tools\index.js`, that pulls open issues from github and updates the tweaks.json file. Just run `npm install`, then `npm start`. If changes were found, commits will be made, then just `git push` to remote.

To use the script, the env variable `GITHUB_API_TOKEN` must be set.

## Calculations

I wanted to make this automated, community driven, with minimal human dependencies. Here is how the statuses are calculated:

 - `Working`: if 75% of the users say it's working. 
 - `Likely working`: if 40% of the users say it's working. 
 - `Not working`: if < 40% say it's working

## Installing

This tweak can be installed with Cydia via the [big boss](http://apt.thebigboss.org/onepackage.php?bundleid=bz.jed.tweakcompatible) repo.

## To-Do

 - Add moderation tools
    - block package / lock package
    - block user
    - block cydia repo
    - delete review
 - Add request feature
 - Never ending scroll, more filters
 - `rebuild` command to rebuild index from closed issues
 - add pagination issue looper
 - minimize json, and split by ios version
 - add webhook processing

## License

Licensed under [Apache License, version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

## Credits

Thanks to [HASHBANG](https://github.com/hbang) for open sourcing the now defunct tweak Pheromone.