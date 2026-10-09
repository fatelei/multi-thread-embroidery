# Video provider notes

Check current tools and schemas before assuming a plugin, model, or parameter is available. The historical workflow used HappyHorse video_edit through qwen-mm-plugins-video-edit. Current tools or official documentation determine supported behavior at execution time.

## Configuration and requests

- Prefer an available generation tool. The historical plugin read `DASHSCOPE_API_KEY` from the environment or `~/.qwen-mm-plugins/config`. Never place credentials in prompts, skills, logs, or deliverables. Ask for local configuration rather than requesting secrets in chat.
- The plugin once cached an empty configuration at startup. If the file exists but the tool reports missing credentials, inspect its loading behavior. Reload the plugin, or use a separate process to call the same verified service when permissions allow. Do not repeatedly request a key or change unrelated settings.
- Direct calls should read the key from the environment or configuration and send it only as an authentication header to the verified provider endpoint. Do not print headers. Follow the runtime's network and configuration-write permission requirements.
- Check the model's media types, dimensions, duration, and size limits. The historical video-edit endpoint accepted video data URLs; this is not a guarantee for other models or future versions. Do not upload private footage to arbitrary file-hosting services for convenience.

## Jobs and errors

- Persist the task ID immediately after submission and poll the same job. Save sanitized prompts, model, parameters, status, and local result paths. Recover an existing job after a timeout or interruption instead of blindly creating another paid job.
- Inspect the footage only after SUCCEEDED and a successful download. Job success does not establish that the user's visual goal was met.
- `Arrearage`: account balance or billing issue. Stop and report it. After the user confirms resolution, verify that the prior job was never created or has failed before submitting again.
- `IPInfringementSuspect`: report the provider's rejection accurately without making your own legal determination. Do not conceal identity, disguise prompts, or repeatedly retry to evade the rejection. If the user explicitly requests an unchanged retry, make one attempt and report its actual result.
- Other failures: distinguish authentication, invalid parameters, and service failures before correcting them. Without a known job status, lack of a result does not establish that no job was created or no charge occurred.

## Delivery

Temporary signed URLs are not permanent deliverable links. Download the result into the task's output directory and preview the actual file. Preserving source audio requires an explicit generation setting or post-processing, followed by verification. Disclose missing audio rather than claiming it was retained.
