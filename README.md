# Codeable Reviews and Expert Profile Plugin

WordPress plugin for front end display of Codeable expert information

Stores expert and review information from the API in transients to lower number of server calls
* Expert Information (1 day)
* Reviews (4 hours)

## Shortcodes (codeable_id att required):

| Shortcodes       | Item to Insert       |
|:------------- |:-------------|
| [expert_reviews codeable_id=31044] | shows reviews |
| [expert_image codeable_id=31044] | profile image |
| [expert_completed codeable_id=31044] | # of completed projects |
| [expert_rating codeable_id=31044] | average rating |
| [expert_hire codeable_id=31044] | button to hire |

## Optional Atts
### Optional atts: expert_reviews
* number_to_pull, defaults to 20, how many reviews to save from the api (can control how many show with show_x_more)
* show_title=yes to show task title, defaults to no
* show_date=yes to show review date, defaults to no
* show_rating=no to hide the rating (default is show)
* min_score, only shows reviews above and including this score (blank is no min)
* max_score, only shows reviews below and including this score (blank is no max)
* sort=rand, sorting options, valid value is just rand for now. Default is no sorting (profile page order)
* start_at (default 1), useful for chunking in offsets. (Does not work for now with random)
* show_x_more (default is show all), show the next x reviews (from offset if set, or from start).
* min_review_length (default is show all), number of characters minimum in review message to show the review. Set to 1 to hide blank reviews, or larger number to hide short reviews. 
* has_picture, set to "yes" to hide all reviews that use the default profile image (may break if default no profile images switches, I will have to fix manually if so)

### Optional atts: expert_image
* circle=yes , default is yes shows image as a circle
* class=your-class , add a custom extra class to the image tag for easier styling

### Optional atts: expert_hire
* message="Your Message", defaults to "Hire Me"
* referoo=xxxxxx, defaults to empty
* class=your-class, optional extra class to add to the link to make styling easier
* theme=black sets a button theme: valid values are black, white, or anything else for no theme (defaults to black)

### No optional atts on expert_completed or expert_rating

## Future Goals / Plans

* Additional sort options
* Impliment a "default" expert ID, referoo code as plugin settings (still could be overwritten on a shortcode level)
* Continue to tweak and optimize code / display as needed
* Look at some sort of local caching of images to cut down on external calls to AWS

== Changelog ==

= 1.3.0 =
* Greatly improved filtering using array_filter (now works with offsets)
* Increased default number to pull to 20
* Handled edge case where user tries to pull more reviews than they actually have
* Better commenting throughout plugin code

= 1.2.1 and 1.2.2 =
* Changed number_to_show to number_to_pull (nonbreaking change)
* Added show_rating=no att to reviews to hide rating / stars line

= 1.2 =
* Add start_at and show_x_more atts on reviews
* Additional filtering atts on reviews: min_review_length, has_picture
* Added changelog

= 1.1 =
* Add support for Github Updater

= 1.0 =
* Added max_score and min_score atts
* Clean up back-end code for saving reviews
* Add random sort option
* Styling fix on review stars

= 0.8 =
* Initial Plugin Release
