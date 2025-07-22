### Product Requirements Document

#### 1. Introduction

This PRD outlines the functional requirements and user experience specifications for a co-working space finder application. The platform aims to connect individuals and teams (End Users) with various co-working and office spaces (Properties) offered by Property Owners. Its core purpose is to facilitate the discovery, comparison, and direct booking of flexible workspace solutions, providing a streamlined experience for both users seeking space and owners listing their properties.

#### 2. User Roles

- **End User (Booker):** Individuals or teams looking to find, compare, and book co-working or office spaces. Their high-level goals include:
  - Searching and filtering available workspaces based on location, amenities, seating options, and pricing.
  - Viewing detailed information about each workspace, including images, descriptions, amenities, and timings.
  - Directly booking available seating options (open seats, cabins, conference rooms) for specified durations.
  - Managing their personal profile and viewing their booking history.
  - Receiving booking confirmations and invoices.
- **Property Owner:** Owners or managers of co-working spaces or office properties who wish to list their spaces on the platform. Their high-level goals include:
  - Creating and managing detailed listings for their properties, including descriptions, images, amenities, and pricing.
  - Defining and updating the availability schedule for their spaces and specific seating options.
  - Receiving notifications for new bookings.
  - Managing their property-specific cancellation policies.
  - Viewing booking records for their properties.
- **Property Moderator:** Internal platform administrators responsible for content moderation and platform oversight. Their high-level goals include:
  - Reviewing and approving/rejecting new workspace listings.
  - Creating new listings on behalf of owners (if necessary).
  - Blacklisting problematic users, properties, or owners.
  - Assisting in dispute resolution through manual communication.

#### 3. Core Features

- **Workspace Listing & Management:** Property Owners can create comprehensive listings for their co-working or office spaces, including descriptive text, tags, images, detailed address, amenities, and operating hours. Owners can manage multiple properties.
- **Flexible Seating Options:** Support for different types of bookable resources within a property: open seats, private cabins, and conference rooms, each with specified capacity.
- **Configurable Pricing Models:** Property Owners can set various pricing options (hourly, daily, weekly, monthly, yearly) for their properties, applicable universally across all seating options within that property.
- **Advanced Search & Filtering:** End Users can search for workspaces using a wide range of filters including city, price range, seating option type, specific amenities, and availability date/time. Initial search results are sorted by distance.
- **Direct Booking System:** End Users can directly book and reserve available spaces for specific durations with instant confirmation.
- **Integrated Payment Gateway:** Facilitation of secure online payments for bookings via a third-party payment gateway (e.g., Stripe, Razorpay).
- **Customizable Cancellation Policies:** Property Owners can define property-specific cancellation policies, overriding a default platform-wide policy (e.g., 24-hour default). A platform fee (10% of the booking amount) will be withheld on cancellations.
- **Availability Management:** Owners can define their weekly operating hours and mark holidays, which automatically updates the availability for all bookable resources within their property. The system will track availability by looking at confirmed bookings.
- **End User Account & Booking History:** Registered End Users maintain a profile and can view a comprehensive history of their upcoming and past bookings, including associated invoices.
- **Property Moderation:** Property Moderators review all new and updated workspace listings to ensure accuracy and adherence to platform standards before they go live. They also have the ability to blacklist users/properties.

#### 4. User Flows

##### User Flow 1: Property Owner Onboarding & Listing a Workspace

1.  **Property Owner registers/logs in.**
2.  **Property Owner navigates to "List a New Property" section.**
3.  **System presents a multi-step form for property details:**
    - **Basic Info:** Property Name, Title, Description, City (mandatory dropdown/text input), Full Address.
    - **Images:** Upload 5-12 images (including selecting a primary image).
    - **Tags:** Select from predefined tags or add custom tags.
    - **Amenities:** Select from a predefined list of available amenities.
    - **Timings:** Set weekly working hours (e.g., Mon-Fri 9 AM - 6 PM) and mark holidays.
    - **Seating Options:** Specify number of `open seats`, `cabins` (with capacity), `conference rooms` (with capacity).
    - **Pricing:** Set `hourly`, `daily`, `weekly`, `monthly`, `yearly` rates. Owners can choose which models to offer.
    - **Cancellation Policy:** Define property-specific cancellation policy, overriding default.
4.  **Property Owner submits the listing.**
5.  **System places the listing in "Under Review" status.**
6.  **Property Moderator reviews the listing.**
7.  **If approved:** Moderator changes status to "Active." System publishes the listing and notifies the Property Owner of approval via email.
8.  **If rejected:** Moderator rejects the listing. System notifies the Property Owner of rejection and reason via email.
9.  **If clarification needed:** Moderator marks for clarification. System notifies Property Owner what needs to be updated. Owner updates and resubmits for review.

##### User Flow 2: End User Searching & Booking a Workspace

1.  **End User accesses the application (can browse as a guest).**
2.  **System displays the Home Screen with a search interface (City input, Date/Time pickers, basic filters).**
3.  **End User inputs desired City, Date, Time, and potentially other filters (e.g., seating option type).**
4.  **User taps "Search."**
5.  **System displays search results, sorted by distance by default.** Each result card shows basic info (Name, Primary Image, City, Price Range).
6.  **End User applies additional filters** (Price Range, Amenities, Specific Seating Options).
7.  **End User taps on a specific workspace listing to view full details.**
8.  **System displays the Workspace Detail Screen** with all property information (description, images, amenities, timings, seating options with availability for the selected date/time, pricing details).
9.  **End User selects a `Seating Option` (e.g., 2 open seats, 1 cabin, 1 conference room) and a `Duration` (e.g., 4 hours, 1 day, 1 month).**
10. **System checks real-time availability for the selected option and duration.**
11. **If available, System displays booking summary and "Book Now" button.**
12. **End User taps "Book Now."**
13. **If End User is not logged in, System prompts for login/registration.**
14. **System navigates to the Payment Gateway.**
15. **End User completes payment.**
16. **System receives payment confirmation from the gateway.**
17. **System updates booking status to "Confirmed," decrements availability for the booked resource, and records the booking.**
18. **System sends booking confirmation (with invoice) to End User via email.**
19. **System sends booking notification to Property Owner via email.**
20. **System navigates End User to a "Booking Confirmed" screen or their "My Bookings" dashboard.**

##### User Flow 3: End User Viewing Booking History

1.  **End User logs in.**
2.  **End User navigates to "My Bookings" section (via dashboard or navigation menu).**
3.  **System displays two lists: "Upcoming Bookings" and "Past Bookings."**
4.  **For each booking, System displays:** Workspace Name, Date/Time, Duration, Seating Option, Amount Paid, and Status (e.g., Confirmed, Completed, Cancelled).
5.  **End User can tap on a booking to view more details or access the invoice.**

##### User Flow 4: Property Owner Managing Availability

1.  **Property Owner logs in.**
2.  **Property Owner navigates to "My Properties" dashboard.**
3.  **Property Owner selects a specific property to manage.**
4.  **Property Owner navigates to "Availability/Calendar" section.**
5.  **System displays a calendar view and weekly schedule interface.**
6.  **Property Owner sets default weekly working hours (e.g., Mon-Fri, 9 AM - 6 PM).**
7.  **Property Owner marks specific dates as holidays.**
8.  **System updates availability across all seating options for that property based on schedule, holidays, and confirmed bookings.**

#### 5. Screen Descriptions & UI Elements

##### 5.1. Home Screen (End User)

- **Purpose:** Initial landing page for users to begin their search.
- **Key UI Elements:**
  - **Header:** Logo/App Name, Login/Sign Up buttons (if not logged in), User Profile icon (if logged in).
  - **Search Bar/Input Fields:** Prominent fields for "City," "Date," "Time," and potentially "Number of people."
  - **"Search" Button:** Clearly visible action button.
  - **Optional:** Featured workspaces or popular cities (for discovery, not functional yet).
- **User Interactions:** Entering search criteria, tapping search button, logging in/registering.

##### 5.2. Search Results Screen (End User)

- **Purpose:** Display a list of workspaces matching the search criteria.
- **Key UI Elements:**
  - **Header:** Search query summary, "Refine Filters" button.
  - **Filter/Sort Bar:** Horizontal scrollable/collapsible section for active filters and sorting options (currently "Distance").
  - **Workspace List:** A scrollable list of cards, each representing a workspace:
    - Primary Image
    - Workspace Name & Title
    - City & Location Summary
    - Brief description snippet
    - Available Seating Options & "Starting From" Price.
    - Distance from user's current location (if location services enabled, otherwise generic sorting).
  - **Pagination:** (If applicable for web)
- **User Interactions:** Scrolling, tapping "Refine Filters," tapping on a workspace card to view details.

##### 5.3. Workspace Detail Screen (End User)

- **Purpose:** Provide comprehensive information about a selected workspace and enable booking.
- **Key UI Elements:**
  - **Header:** Workspace Name, "Back" button.
  - **Image Carousel:** High-quality images of the workspace.
  - **Basic Info:** Name, Title, Address, City.
  - **Description:** Detailed text about the workspace.
  - **Amenities Section:** List of available amenities (checkbox/icon representation).
  - **Timings Section:** Display of weekly operating hours and marked holidays.
  - **Seating Options Section:**
    - List of available types (Open Seats, Cabins, Conference Rooms).
    - For each type: Capacity, current Availability for selected date/time.
    - Price for each type (hourly, daily, etc.).
    - **Selection Controls:** Input for "Number of Seats/Rooms," "Duration" (e.g., hours, days, months), and "Date/Time" pickers.
  - **"Book Now" Button:** Enabled only when a valid selection is made and space is available.
  - **Cancellation Policy Display:** Summary of the property's cancellation terms.
- **User Interactions:** Swiping through images, scrolling through details, selecting seating options/duration/date/time, tapping "Book Now."

##### 5.4. End User Dashboard / My Bookings Screen

- **Purpose:** Provide an overview of upcoming and past bookings.
- **Key UI Elements:**
  - **Header:** "My Bookings."
  - **Tabs/Sections:** "Upcoming Bookings," "Past Bookings."
  - **Booking List:** Each item represents a booking:
    - Workspace Name, Location
    - Booking Date & Time, Duration
    - Seating Option Type & Quantity
    - Total Price
    - Booking Status (e.g., Confirmed, Completed, Cancelled)
    - "View Details / Invoice" button.
- **User Interactions:** Tapping on booking items to view more details.

##### 5.5. Property Owner Dashboard

- **Purpose:** Central hub for owners to manage their listed properties.
- **Key UI Elements:**
  - **Header:** "Owner Dashboard," "Add New Property" button.
  - **Property List:** Cards for each owned property:
    - Property Name, City.
    - Summary of active bookings.
    - "Manage Property" button (links to specific property management).
    - "View Bookings" button (links to property-specific booking history).
    - "Edit Listing" button.
    - Status (e.g., Active, Under Review, Draft).
- **User Interactions:** Tapping buttons to manage properties, add new listings.

##### 5.6. Property Management Screen (Owner)

- **Purpose:** Edit details, manage availability, and view bookings for a specific property.
- **Key UI Elements:**
  - **Header:** Property Name, "Back" button.
  - **Tabs/Sections:** "Listing Details," "Availability," "Bookings."
  - **Listing Details Tab:** Editable form with all property attributes (similar to creation, but pre-filled).
  - **Availability Tab:** Calendar view for setting hours and marking holidays.
  - **Bookings Tab:** List of all past and upcoming bookings for this specific property.
- **User Interactions:** Editing fields, saving changes, managing calendar, viewing bookings.

#### 6. Functional Specifications

##### 6.1. User Account Management (End User)

- **Input:** Email, Password, Name, Phone Number (for registration/profile update).
- **Output:** Registered user account, updated profile information.
- **System Behavior:**
  - Allows registration via email/password.
  - Stores `name`, `email`, `phone_number`, `booking_history`. (Other necessary items might include: preferred city, company name if booking for team, payment method details securely tokenized).
  - Allows users to update their profile information.
  - "Forgot Password" flow via email.
  - End users _must_ be logged in to book a space.

##### 6.2. Workspace Listing (Property Owner)

- **Input:** `name`, `title`, `description`, `images` (min 5, max 12, primary image selection), `city`, `full_address`, `amenities` (predefined list selection), `weekly_timings` (Mon-Sun working hours), `holidays` (specific dates), `seating_options` (type, capacity), `pricing` (hourly, daily, weekly, monthly, yearly, per seating option type), `cancellation_policy_text`.
- **Output:** New `workspace_listing` record in "Under Review" status.
- **System Behavior:**
  - Associates listing with Property Owner's account.
  - Performs input validation for all fields.
  - Generates a `geohash` from the `address` for internal use.
  - Initial status is "Under Review."

##### 6.3. Property Moderation

- **Input:** `workspace_listing_id`, Moderator action (`approve`, `reject`, `clarification`).
- **Output:** Update to `workspace_listing.status`, owner notification.
- **System Behavior:**
  - **Approve:** Sets `workspace_listing.status` to "Active." Makes listing discoverable. Notifies owner.
  - **Reject:** Sets `workspace_listing.status` to "Rejected." Provides reason. Notifies owner.
  - **Clarification:** Sets `workspace_listing.status` to "Pending Clarification." Notifies owner of required updates.
  - **Blacklist:** Moderator can set `user_status` or `property_status` to "Blacklisted," preventing listing/booking activity.

##### 6.4. Search and Filter (End User)

- **Input:** `city` (mandatory), `date_range`, `time_range`, `price_min`, `price_max`, `seating_type_filter` (open, cabin, conference), `amenity_filter_ids`, `tags_filter_keywords`.
- **Output:** Filtered and sorted list of `active_workspace_listings`.
- **System Behavior:**
  - Queries `active` listings.
  - Uses `geohash` for efficient location-based filtering and distance calculation.
  - Filters results by `availability` for the selected date/time.
  - Sorts results by `distance` from the user's inferred/selected location by default.
  - Supports combining multiple filters.

##### 6.5. Availability Management

- **Input:** `property_id`, `weekly_schedule` (day-wise hours), `holiday_dates`.
- **Output:** Updated `property_availability_rules`.
- **System Behavior:**
  - Stores `operating_hours` for each day of the week.
  - Stores specific `holiday_dates` when the property is closed.
  - `Availability Engine`: Dynamically calculates available capacity for each `seating_option` at any given `date` and `time` by:
    - Checking `operating_hours` and `holidays`.
    - Subtracting `booked_capacity` from `total_capacity` based on confirmed `bookings`.

##### 6.6. Booking & Payment

- **Input:** `user_id`, `workspace_id`, `seating_option_type`, `quantity`, `start_datetime`, `end_datetime`, `duration_type` (hourly/daily/etc.), `total_price`.
- **Output:** `booking` record (status: "Pending Payment" -> "Confirmed"), `payment_transaction` record, notifications, updated availability.
- **System Behavior:**
  - Before payment, performs final check for `availability`.
  - Integrates with chosen `payment_gateway` (e.g., Razorpay, Stripe) for secure transaction processing.
  - On successful payment:
    - Creates a `booking` record with "Confirmed" status.
    - Generates a unique `invoice_id`.
    - Updates `available_capacity` for the booked `seating_option` and `time_slot`.
    - Sends `booking_confirmation_email` (with invoice) to End User.
    - Sends `booking_notification_email` to Property Owner.
  - On payment failure: Notifies user, clears pending booking.

##### 6.7. Cancellation

- **Input:** `booking_id`, `user_id` (initiating cancellation).
- **Output:** `booking_status` changed to "Cancelled," `refund_transaction` (if applicable), notifications, updated availability.
- **System Behavior:**
  - Checks the `property_cancellation_policy` for the specific booking.
  - Calculates `refundable_amount` based on policy and booking time relative to start time.
  - Initiates `refund` via payment gateway (less the 10% platform fee).
  - Updates `booking_status` to "Cancelled."
  - Adds `cancelled_capacity` back to `available_capacity` for the relevant `seating_option` and `time_slot`.
  - Notifies End User of cancellation and refund status.
  - Notifies Property Owner of cancellation.

#### 7. Non-Functional Requirements (UX/Performance Focus)

- **Responsiveness:** The application must be fully responsive, providing an optimal user experience across desktop browsers, tablets, and mobile devices (both portrait and landscape orientations).
- **Ease of Use:** The user interface should be intuitive for both End Users (searching, booking) and Property Owners (listing, managing). Forms should be clear with appropriate validation and helpful prompts.
- **Loading Times:**
  - Initial page load: Under **3 seconds**.
  - Search results display: Under **2 seconds**.
  - Workspace detail page load: Under **2 seconds**.
  - Booking confirmation after payment: Under **3 seconds**.
  - Image uploads (for owners): Max **5 seconds** per image.
- **Visual Feedback:** Provide immediate and clear visual feedback for all user interactions, including button presses, form submissions, successful bookings, validation errors, and loading states.
- **Accuracy of Availability:** The availability system must be highly accurate and reflect real-time booking status to prevent overbooking.
- **Payment Reliability:** The payment gateway integration must be robust and handle payment success/failure scenarios gracefully, providing clear feedback to the user.
- **Notification Reliability:** Booking confirmations, owner notifications, and cancellation updates must be sent reliably and promptly via email/WhatsApp.
- **Search Performance:** The search and filtering mechanism should be highly performant, even with a large number of listings, leveraging `geohash` efficiently.
- **Data Integrity:** All booking, pricing, and availability data must be consistent and accurate across the platform.
- **Error Handling:** User-friendly error messages should be displayed for all invalid inputs, network issues, or system errors, guiding the user on how to proceed.
- **Scalability:** The platform should be designed to handle a growing number of users, properties, and daily bookings without performance degradation.
