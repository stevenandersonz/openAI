# Prompting LLM - Reasoning about API

The purpose was to prompt Davinci-003 and GPT3.5-turbo in two ways:

- Finding hidden task between inputs and outputs
- Use task to program the LLM at inference and retrieve its outputs

The project involved prompting the LLMs in two ways - first, finding hidden tasks
between inputs and outputs, and second, reprogramming the LLMs to read endpoint data
and output a standardized document for the API (I got an almost valid JSON output).

# Thoughts on OUTPUTS

1. My favorite was the output from `01.prompt.txt`

```json
[
  {
    path: "/todos",
    method: "GET",
    description: "Get all todos",
    request: {},
    response: {
      title: String,
      description: String,
      completed: Boolean
    }
  },
  {
    path: "/todos",
    method: "POST",
    description: "Create a new todo",
    request: {
      title: String,
      description: String,
      completed: Boolean
    },
    response: {
      title: String,
      description: String,
      completed: Boolean
    }
  },
  {
    path: "/todos/:id",
    method: "GET",
    description: "Get a single todo",
    request: {},
    response: {
      title: String,
      description: String,
      completed: Boolean
    }
  },
  {
    path: "/todos/:id",
    method: "PUT",
    description: "Update a todo",
    request: {
      title: String,
      description: String,
      completed: Boolean
    },
    response: {
      title: String,
      description: String,
      completed: Boolean
    }
  }
]
```

2. The output from `00.prompt.txt` using davinci-003 is also good is you are looking for a more simple result

Route 1:
Method: GET
Description: Retrieve all todos
Request: /todos
Response: Todos

Route 2:
Method: POST
Description: Create a new todo
Request: /todos
Response: Todo

Route 3:
Method: GET
Description: Retrieve a single todo
Request: /todos/:id
Response: Todo

Route 4:
Method: PUT
Description: Update a single todo
Request: /todos/:id
Response: Todo

```

```
