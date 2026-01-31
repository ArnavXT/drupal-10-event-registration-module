# Events Manager

A custom Drupal 10 module for managing event registrations.

## Features
- Admin interface to create events with categories and date ranges.
- Public registration form with AJAX-dependent fields (Category -> Date -> Event).
- Validation: No special chars, duplicate email check per event.
- Admin dashboard to view registrants, filter by date/event, and export to CSV.
- Email notifications for users and admins.

## Installation
1. Clone this repository into `web/modules/custom/`.
2. Run `composer install` (if dependencies exist) or ensure structure is correct.
3. Enable the module via Drush: `drush en events_manager -y`.
4. The database tables `events_manager_event` and `events_manager_registration` will be created automatically.

## Setup & Configuration
1. **Global Settings**: Go to `/admin/config/services/events-manager/settings` to configure the Admin Notification Email and enable/disable notifications.
2. **Add Events**: Go to `/admin/config/services/events-manager/add-event` to create new events. Ensure you set the "Registration Start/End Dates" correctly, as the public form filters events based on the current date.

## Usage
- **Registration Form**: The public form is located at `/events/register`.
- **Admin Listing**: View and export registrations at `/admin/content/events-registrations`.

## Database Schema
- **events_manager_event**: Stores event metadata (Name, Category, Dates).
- **events_manager_registration**: Stores participant data with a Foreign Key linking to the event ID.

## Technical Details
- Implements `FormBase` and `ConfigFormBase`.
- Uses Dependency Injection for Database, Config, and Mail services.
- PSR-4 compliant.