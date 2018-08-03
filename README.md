# trellis-simple-sync
Ansible playbooks for Trellis database and uploads sync.\
Just copy and run without any extra configuration.

## Installation
1. Copy `database.yml` and `uploads.yml` files into Trellis root folder
2. Copy `bin/sync.sh` files into Trellis bin folder
3. (Optional) Add `*_db_backup.sql.gz` to your Bedrock `.gitignore` file

## Usage
Run `./bin/sync.sh <environment> <site name> <type> <mode>`

* Available `<type>` options: `uploads`, `database`
* Available `<mode>` options: `push`, `pull`
* The `push` is for upload data from development and update selected environment, and the `pull` for download data from selected environment and update development.
* `uploads` sync is not destructive, it only adds or update new files, don't delete missing files.

## Aliases
You can use alias for a shorter or more intuitive commands

* staging - stag - s
* production - prod - p
* database - db
* uploads - media
* push - up
* pull - down

Examples:\
`./bin/sync.sh stag example.com db up`\
`./bin/sync.sh prod example.com media down`

## Notes
* Tested up to Ansible 2.6.1
* For database sync the development vagrant VM must be powered on every time you run a command
* On every database command a `sitename_db_backup.sql.gz` file is automatically created inside destination environment Bedrock folder. In development, if you don't want it to be saved in the repository:
    * You can add `*_db_backup.sql.gz` to your Bedrock `.gitignore` file
    * Or you can comment `PULL > Backup development database` task on `database.yml`

## Contribute
* Anyone is welcome to contribute to the plugin.
* Please merge (squash) all your changes into a single commit before you open a pull request.

## License
MIT

## Credits
© 2018 [Creame](https://crea.me).
Heavily inspired by [trellis-database-uploads-migration](https://github.com/valentinocossar/trellis-database-uploads-migration) and [trellis-db-push-and-pull](https://github.com/hamedb89/trellis-db-push-and-pull).

Special thanks to [the Roots team](https://roots.io/about/) whose [Trellis](https://github.com/roots/trellis) make this project possible.
