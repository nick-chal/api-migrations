# API Migrations

This project tracks current desired versions for all tracks used by the default Reaction Platform. You can fork it to get started but you will likely diverge as you add, remove, and change the Reaction API plugins you use.

This repo was created by following [these instructions](https://github.com/reactioncommerce/migrator#usage). If you don't want to fork this, you can build your own data version tracking project using those steps.

## Local Development Usage

1. Fork/clone this repo.
2. Check out the branch that corresponds to your version of Reaction Platform. (Only 3.0.0 and higher are supported.)
3. `npm install`
4. Then to see a report of necessary migrations for your local MongoDB database and optionally run them:

    ```sh
    MONGO_URL=mongodb://localhost:27017/reaction migrator migrate
    ```

    Use a different `MONGO_URL` to run them on a different database.
5. Refer to [https://github.com/reactioncommerce/migrator](https://github.com/reactioncommerce/migrator) docs for other commands.

## Migrating Deployment Databases

You can follow "Local Development Usage" and specify a remote database if you want. Migrations will run on your computer, which may not be very fast or reliable.

Instead, you can set up a CI task for this repo.

1. Create different configuration files for each deployed environment. For example, `migrator.config-staging.js` for the "staging" environment.
2. Add the necessary `MONGO_URL`s to your CI environment/secrets.
3. When config file changes are merged to the main branch, run `migrator migrate <env> -y` as a CI task with `MONGO_URL` set to the correct database for that environment.

## Developer Certificate of Origin
We use the [Developer Certificate of Origin (DCO)](https://developercertificate.org/) in lieu of a Contributor License Agreement for all contributions to Reaction Commerce open source projects. We request that contributors agree to the terms of the DCO and indicate that agreement by signing-off all commits made to Reaction Commerce projects by adding a line with your name and email address to every Git commit message contributed:
```
Signed-off-by: Jane Doe <jane.doe@example.com>
```

You can sign-off your commit automatically with Git by using `git commit -s` if you have your `user.name` and `user.email` set as part of your Git configuration.

We ask that you use your real full name (please no anonymous contributions or pseudonyms) and a real email address. By signing-off your commit you are certifying that you have the right to submit it under the [Apache 2.0 License](./LICENSE).

We use the [Probot DCO GitHub app](https://github.com/apps/dco) to check for DCO sign-offs of every commit.

If you forget to sign-off your commits, the DCO bot will remind you and give you detailed instructions for how to amend your commits to add a signature.

## License
Copyright 2020 Reaction Commerce

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and
limitations under the License.
