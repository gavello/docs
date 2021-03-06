![SeAT](https://i.imgur.com/aPPOxSK.png)

# Getting Started

So you have decided to manually install SeAT, before you start it would be a good idea to review what you need first. Once you have done this, head to the corresponding installation guide in the sidebar left which fits your setup best.

## Manual Installation

!!! warning

    Make sure you review the hardware and software requirements sections before installing anything intended for production use!

## General Instructions

Finally, you can always install SeAT manually. You will need to get PHP 7.1, MariaDB, Redis and a web server such as nginx running. Guides for popular Linux distributions such as Debian, Ubuntu and CentOS can be found in the sidebar, but if those distributions aren't your cup of tea, follow these steps to get going:

- Install PHP 7.1.
- Install the latest MariaDB / MySQL server.
- Install Redis server.
- Install the [composer](https://getcomposer.org/) PHP dependency manager.
- Choose where you want the SeAT sources to live and start the download with `composer create-project eveseat/seat`.
- Once installed, `cd` to the new `seat/` directory and publish migrations and assets with `php artisan vendor:publish --force --all`.
- If you want the Swagger API documentation, run `php artisan l5-swagger:generate`.
- Update the `.env` file with your database settings. Ideally SeAT should have full control over only its own database (not the entire database server);
- Run the database migrations with `php artisan migrate`.
- Update the EVE Static Data tables with `php artisan eve:update:sde -n`.
- Run the SeAT schedule seeder with `php artisan db:seed --class=Seat\\Services\\database\\seeds\\ScheduleSeeder`.
- Configure a web server to serve the `public/` directory to the world.
- Download supervisord and have it keep the `php artisan horizon` command alive. This will allow you to process jobs.