FROM node:14.16.0

# update this line when gatsby-gitbook-starter repo changes
RUN sh -c 'echo -e "Updated at: 2021-03-25 21:00:00 IST"'

# Install global dependencies
RUN npm -g install gatsby-cli

# clone gatsby-gitbook-starter repo
RUN git clone https://github.com/hasura/gatsby-gitbook-starter.git
RUN cd gatsby-gitbook-starter && git checkout gitbook-theme-hasura

# Create app directory
WORKDIR /gatsby-gitbook-starter

RUN cd /gatsby-gitbook-starter

# Install dependencies
RUN npm ci

# Remove already existing dummy content
RUN rm -R content

# Bundle app source
COPY . .

# Build static files
RUN GATSBY_ALGOLIA_APP_ID=WCBB1VVLRC GATSBY_ALGOLIA_SEARCH_KEY=0301b192e18d1598fde3095dc721bdba npm run build

# serve dist folder on port 8080
CMD ["gatsby", "serve", "--verbose", "--prefix-paths", "-p", "8080", "--host", "0.0.0.0"]
