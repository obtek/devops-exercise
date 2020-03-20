# BrightHive Engineering Coding Exercise

## Task Outline

We've just landed a brand new contract with **Super Hero University** to build a [Data Trust](https://brighthive.io/#data-trust-description) that will help heroes across the various universes (Marvel, DC, Dark Horse) to share information about the skills and abilities possessed by superheroes.

Your task will be to build a simple API that provides the following features:

- Add a new superhero.
- Retrieve an existing superhero by a unique identifier.
- Search for various superheroes in the system based on different criteria.

### Data Format

The application should accept and produce JSON with the appropriate content types.

### Data Structure

In general, a superhero object will contain the following data fields:

- An `id` field that uniquely identifies the superhero. This should be provided by the server when the hero is created and cannot be changed.
- A `superhero_alias` field that provides the superhero's alias (e.g Wonder Woman, Batman, Captain Data). This field must be non-blank and unique.
- An `email_address` field for the superhero's contact email. This field is optional, but must be unique within the field when provided. The application should verify that the `email_address` field is superficially valid.
- A `first_name` field representing the superhero's first name. This field is required and cannot be blank.
- A `last_name` field representing the superhero's last name. This field is optional.
- A `started_on` field representing the date the superhero enrolled in Super Hero University. This field should be formatted as YYYY-MM-DD and when not specified, should automatically populate with the date the superhero was added to the system.
- A `finished_on` field representing when the superhero graduated from Super Hero University. This field is optional (absence of a date indicates the student is still enrolled). When provided, the field should be formatted as YYYY-MM-DD.
- A `status` field that indicates the superhero's current academic staus, such as 'Active', 'Expelled', 'Graduated', etc. This field is required.
- An `income` field that represents the superhero's current income. This field is optional and should be able to hold decimal numbers.

### API Routes

The following routes are required for this API:

- **Create a new superhero**:`POST  /heroes`. Returns a 201 status on success.
- **Search for superheros**: `GET /heroes`. Returns a 200 status on success.
- **Retrieve a specific superhero**: `GET /heroes/{id}` (where `{id}` is the unique identifier supplied by the system). Returns a 200 status on success, 404 status on no match found.
- **API Health**: `GET /api/health`. Returns a 201 status if the API is active.

### Search

The superheros may be searched by the following fields:

- `started_after` - Superheroes who started after a specific date (formatted as YYYY-MM-DD).
- `started_before` - Superheroes who started before a specific date (formatted as YYYY-MM-DD).
- `finished_after` - Superheroes who finished after a specific date (formatted as YYYY-MM-DD).
- `finished_before` - Superheroes who finished before a specific date (formatted as YYYY-MM-DD).
- `income_below` - Superheroes with income below a specific integer value.
- `income_above` - Superheroes with income above a specific integer value.
- `income_equal` - Superheroes with income equal to a specific integer value.
- `status` - Superheroes with a specific status.

If  multiple fields are provided, any records returned must match all of them. That is, you should treat them as `AND`. For example, the query below should return all superheroes who started Super Hero University after November 1, 2018 who have a 'Graduated' status and earn above $275,000 but below $300000.

```bash
GET /heroes?started_after=2018-11-01&status='Graduated'&income_above=275000&income_below=300000
```

### General Notes

During the engineering discussion, we will talk about your code and decisions you've made. We may also challenge assumptions you've made about the problem or discuss other requirements, such as:

- How would we handle changes to superhero data?
- What if we wanted to track the various courses that superheroes took and the superpowers acquired from each course.
- How could we handle multiple versions of this API?
- What could we do to limit the results provided by the API?

### Environmental Constraints

#### 1. Programming Language

All source code must be implemented in Python 3. For implementing the API we recommend using [Flask-Restful](https://flask-restful.readthedocs.io/en/latest/) although pure [Flask](http://flask.pocoo.org/) is perfectly acceptable.

#### 2. Docker

Your solution must run as a Docker container. There is a starter `docker-compose.yml` file included in this project that can be used to run the solution with a PostgreSQL database backend. There is also a `Dockerfile` that can be modified to build the Docker image for the project.

All external dependencies should be captured by a standard dependency management tool such as `pip` with an appropriate `requirements.txt` file or `Pipenv` (we use Pipenv here).

We should be able to launch your application by simply executing the command `docker-compose up` and build it by using the command `docker-compose build`.

### 3. Unit Testing

Your application should at a minimum provide unit tests for the API search endpoints. These unit tests do not need to run inside of Docker; however, you must provide documentation on how to run those tests. Please use a standard unit testing library such as `unittest` or `pytest` for writing your unit tests.

### 4. Documentation

Please provide some documentation on how to run your application as well as any issues or caveats to consider with your implementation. Also be sure to note any critical items that you want the engineering team to know about during the review of your code.

## Freestyle (Optional)

Ok, now that you've implemented the new API for our Super Hero University Data Trust, you now have the flexibility to do something additional with the API to showcase some of your other skills and interests that you would like us to know about. Please limit this to one additional task. Tasks may include things such as:

- Implement a quick and simple web application that consumes data from the API.
- Deploy the API to a Cloud service such as AWS.
- Add another API endpoint that does something creative with the data.
- Implement a basic security mechanism for the API.
- Write an OpenAPI specification for the API.

These are just a few of the many ideas that you could pursue, but this is all up to your imagination. Also note that this section is totally optional.