# spiritual-gifts

a quiz to determine a good place to serve in the church

## dev planning

-   sqlite db
-   Laravel/Vue stack
-   Docker deployment?

## needs

-   list of questions

## mvp user flow

-   User loads page
-   Enters email address to which quiz results will be bound
-   User goes through each question, selecting an answer from 1-5
-   And the end of the quiz the user will see a screen with their results
    -   top 3 results larger at the top
    -   next 12 results in smaller list below
    -   export as image
-   Users can return and access their results using their email address
    -   user auth via email verification as log in?

## todo

-   DB tables:
    -   users: `email`, `quiz_results`
        -   quiz_results = string of tallied scores (i.e. a8,b12,c3...)
        -   each result will default to a score of 0 if the question has not been answered yet
    -   questions: `text`, `gift`
-   Build create user page
    -   This should be the default page
    -   Contains:
        -   email form (validate email format)
        -   submit button
    -   Behavior:
        -   on submit, find or create user
        -   send email for auth (not mvp)
        -   store user in state
        -   Go to quiz page
-   Build quiz page
    -   This should not load if user has not been loaded
    -   Contains:
        -   Question text
        -   slider from 1-5
        -   Prev and Next buttons
        -   Progress bar
-   Build results page
    -   only load if all questions have been answered
    -   contains:
        -   Top 3 gifts large text
        -   Remaining top 10 gifts in smaller text
        -   tab to list of all 26 gifts and scores
        -   export button for top 10 gifts as image

## Get it running locally

This assumes that you have php and Laravel installed locally already. If not follow the instructions at [Laravel.com](https://laravel.com/docs/11.x/installation)

```
composer install
php artisan migrate
php artisan key:generate
npm install && npm run build
composer run dev
```
