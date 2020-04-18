# Build and Publish PDF from LaTeX file
![Build LateX](https://github.com/rishabhverma17/DevOpsing_Resume/workflows/Build%20LateX/badge.svg?branch=master)

![Build LateX Resume 2](https://github.com/rishabhverma17/DevOpsing_Resume/workflows/Build%20LateX%20Resume%202/badge.svg)

Here's what *you* need to do if you want to compile your LaTeX document in the cloud with [GitHub Actions](https://github.com/actions/).

- Sign up for GitHub Actions and turn them on for a repository containing your [LaTeX](https://www.latex-project.org/) code
- I assume you want to have the generate PDF in the same repository as the one you're working on [1]
- Generate a `gh-pages` branch for your repository and make sure it's being served by [GitHub pages](https://pages.github.com/) by going to 'Settings' > 'Options' in your repository
- Generate an SSH key to use for deployment:
  - Do this with
  ```bash
  cd && mkdir tmp && cd tmp
  ssh-keygen -t ed25519 -o -a 100 -f actions_key
    ```
  - Go to 'Settings' > 'Deploy keys' and copy the contents of the public key (`actions_key.pub`) to the form field.
  - Go to 'Settings' > 'Secrets' and copy the contents of the private key (`actions_key`) to a new secret. Name this secred `DEPLOY_KEY`.
    This makes sure that the key is correctly picked up by the GitHub Action below.
- Copy the [`main.yaml` file from here](https://github.com/rishabhverma17/DevOpsing_Resume/blob/master/.github/workflows/main.yml) to `$your_repository/.github/workflows/main.yaml`.
   - You can name the output PDF file however you want.
   - Change the settings in the file relating to your Git `user.name`and `user.email`.
   - Change the directory where you would keep all the LaTeX file
   - Change the name of LaTex file and keep the name of PDF in check PDF section same as main file of .tex
   - Also take care that the file name of the LaTeX file is the same as the one you actually use in your repository.
- Commit a good version of your LaTeX file and wait a bit
- Enjoy your automatically built PDF at [$username.github.io/$your_repository/Resume_RishabhVerma_SDE.pdf ](https://rishabhverma17.github.io/DevOpsing_Resume/Resume_RishabhVerma_SDE.pdf)


# How to use this 

- Fork project.
- Checkout branch **development**.
- Do required changes in resume/**tex** files.
- Push to origin
- Merge the branch to Master.
- Pipeline would start building the project.
- After successful build, PDF would be available under branch gh-pages.
