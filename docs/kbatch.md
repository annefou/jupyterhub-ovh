# Enabling kbatch in your Jupyterhub

- Document kbatch —> values.yaml (kbatch section) kbatch_users
- When willing to control resources for users:
- Not implemented the limit per job per user. Can be added if necessary. See kbatch documentation. See namespace customisation.
- katch-proxy —> profiles.yaml (content is inlined) it will be an extra resources.  Can limit number of jobs per user (each user get the same limit).

