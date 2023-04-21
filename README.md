Golem-GPT 
=========

Golem powered by OpenAI GPT.

![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/dingolytics/golem-gpt?sort=date)


Overview
--------

⚠️ **This is an experimental development. Run it on your own risk!** ⚠️

Golem-GPT builds and executes an actionable pipeline to achieve goals
specified by user. Powered by GPT-3.5 or GPT-4 by [OpenAI](https://openai.com).

### Why?

**How is it different from [AutoGPT](https://github.com/Significant-Gravitas/Auto-GPT)?**

We build it because we like it. Our implementation is not as advanced
as AutoGPT to the moment, but it has some unique focus:

- Keeping it simple and easy to modify, also with minimal dependencies
- While keeping the core simple, we aim to make it extensible via custom
  actions, roles, policies, and other components
- We think of it as interactive tool, not necessarily to be fully autonomous
- Also we test it with GPT-3.5, which porbably sounds not super-hyped,
  but it's waaay cheaper and delivers results good enough for many use cases
- We are going to utilize it in our own development cycle, and refine it
  to fit real needs in software development


Requirements
------------

- Docker or Python 3.8+ environment
- OpenAI API key


Usage
-----

The optimal way to run Golem-GPT is to use the [Docker image](https://hub.docker.com/r/dingolytics/golem-gpt) or Docker Compose:

```bash
docker compose build
docker compose run app
```

It's also better to run it inside Docker to have it isolated. Because
Golem can access an environment and filesystem, so it's better to keep
it inside a container.


Actions supported
-----------------

The pipeline consists of the following actions:

- [x] ask_human_input(query)
- [x] get_datetime()
- [x] get_local_date()
- [x] read_file(filename)
- [x] write_file(filename, content)
- [x] http_request(url, method, headers, body, to_filename)
- [ ] create_python_script(name, description, in_files, out_files)
- [ ] create_shell_script(name, description, in_files, out_files)
- [x] run_script(name)
- [ ] ask_google(query, to_filename)
- [ ] delegate_job(goal, role, in_files, out_files)
- [x] explain(comment)
- [x] reject_job(message)
- [x] finish_job(message)


Development
-----------

Setup virtualenv:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip pip-tools
pip-compile
pip install -r requirements.txt
```

Put variables to `.env`:

```bash
OPENAI_API_KEY=...
OPENAI_ORG_ID=...
```

Start a new job:

```bash
python -m golemgpt
```

Continue saved job:

```bash
python -m golemgpt -j <job key>
```

Terminate simply with ^C or empty input.


License
-------

Golem-GPT is licensed under the [Apache-2.0](LICENSE).
