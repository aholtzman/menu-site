# Steps for building this project -

## Setup

cli - start project
  * gatsby new project-name
  * cd project-name

cli - add dependancies
  * styled components
    * yarn add gatsby-plugin-styled-components styled-components babel-plugin-styled-components
  * netlify cms
    * yarn add netlify-cms-app gatsby-plugin-netlify-cms
  * working with the markdown files produced from Netlify CMS
    * yarn add gatsby-source-filesystem gatsby-transformer-remark

cli - add files and folders for NetlifyCMS
  * mkdir -p ./static/admin
  * mkdir -p ./static/img
  * mkdir -p ./src/items/markdown
  * touch ./static/admin/config.yml

add to gatsby-config file plugins array
  * `gatsby-plugin-netlify-cms`
  * `gatsby-plugin-styled-components`
  *  In the YAML config file, for each collection you will need to add the path designated in `folder`
    {
        resolve: `gatsby-source-filesystem`,
        options: {
          path: `${__dirname}/src/items/markdown`,
          name: `markdown-pages`,
        },
      },
  * `gatsby-transformer-remark`,

create a repo for the project on GitHub and push changes

## Configure YAML for the backend

see the [Netlify Widget](https://www.netlifycms.org/docs/widgets/) documentations for additional options/fields

refer to src/admin/config.yml for how this file was setup.

stop your local build and restart it with `yarn start`.

Now when you visit http://localhost:8000/___graphql you can find `allMarkdownRemark` this will be the data source derived from the markdown files saved from the CMS.

## Add some data to get started with

When you add information within the CMS it will be stored as a markdown file in your GitHub repo. To work with this locally, you will need to do a `git pull` after publishing new content to use it.

Visit http://localhost:8000/admin/ in your browser, you will need to log in to and allow access to your GitHub account. Add at least one entry to each collection you have setup in your YAML file so you have something to work with when putting together the front end.
