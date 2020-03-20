# BrightHive DevOps Exercise

## Project Scenario

We've just landed a brand new contract with **Super Hero University** to build a [Data Trust](https://brighthive.io/#data-trust-description) that will help heroes across the various universes (Marvel, DC, Dark Horse) to share information about the skills and abilities possessed by superheroes. We've constructed a RESTful API that supports the following features:

- Add a new superhero.
- Retrieve an existing superhero by a unique identifier.
- Search for various superheroes in the system based on different criteria.

 A superhero request/response object will contain the following fields:

- An `id` field that uniquely identifies the superhero. This should be provided by the server when the hero is created and cannot be changed.
- A `superhero_alias` field that provides the superhero's alias (e.g Wonder Woman, Batman, Captain Data). This field must be non-blank and unique.
- An `email_address` field for the superhero's contact email. This field is optional, but must be unique within the field when provided. The application should verify that the `email_address` field is superficially valid.
- A `first_name` field representing the superhero's first name. This field is required and cannot be blank.
- A `last_name` field representing the superhero's last name. This field is optional.
- A `started_on` field representing the date the superhero enrolled in Super Hero University. This field should be formatted as YYYY-MM-DD and when not specified, should automatically populate with the date the superhero was added to the system.
- A `finished_on` field representing when the superhero graduated from Super Hero University. This field is optional (absence of a date indicates the student is still enrolled). When provided, the field should be formatted as YYYY-MM-DD.
- A `status` field that indicates the superhero's current academic staus, such as 'Active', 'Expelled', 'Graduated', etc. This field is required.
- An `income` field that represents the superhero's current income. This field is optional and should be able to hold decimal numbers.

The following routes are supported by the API:

- **Create a new superhero**:`POST  /heroes`. Returns a 201 status on success.
- **Search for superheros**: `GET /heroes`. Returns a 200 status on success.
- **Retrieve a specific superhero**: `GET /heroes/{id}` (where `{id}` is the unique identifier supplied by the system). Returns a 200 status on success, 404 status on no match found.
- **API Health**: `GET /api/health`. Returns a 201 status if the API is active.

The superheros may be searched by the following fields:

- `started_after` - Superheroes who started after a specific date (formatted as YYYY-MM-DD).
- `started_before` - Superheroes who started before a specific date (formatted as YYYY-MM-DD).
- `finished_after` - Superheroes who finished after a specific date (formatted as YYYY-MM-DD).
- `finished_before` - Superheroes who finished before a specific date (formatted as YYYY-MM-DD).
- `income_below` - Superheroes with income below a specific integer value.
- `income_above` - Superheroes with income above a specific integer value.
- `income_equal` - Superheroes with income equal to a specific integer value.
- `status` - Superheroes with a specific status.

## Deployment Task

Your task is to take the API and deploy it along with other supporting applications needed to run it (e.g. PostgreSQL). The application can be found at [https://github.com/gregmundy/trust-in-superheroes](https://github.com/gregmundy/trust-in-superheroes).

1. Clone the repository
2. Identify the dependencies needed to run the project.
3. Build the Docker image.
4. Write K8s deployments to stand up the API container, supporting applications, and networking needed to expose the API (currently running on port 8000).

### General Notes

During the engineering discussion, we will talk about your deployments and decisions you've made. We may also challenge assumptions you've made about the problem or discuss other requirements, such as:

- What tools would you want to deploy on the cluster to support logging and monitoring?
- How would you handle scaling of services?
- How would you manage upgrades to services?
- What would you do to manage application secrets?

### Environmental Constraints

#### 1. Docker and K8s

In the absence of a real K8s cluster, it is anticipated that the deployment will run locally via [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/).

## Freestyle (Optional)

Now that you have the API and support services deployed, deploy a few of your favorite logging and monitoring tools to support health checks on the cluster and the services. You may either choose to do this by creating manual deployments or using [Helm](https://helm.sh/) charts.
