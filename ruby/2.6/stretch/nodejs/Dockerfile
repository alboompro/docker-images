FROM alboom/ruby-k8s-production:2.6-stretch

RUN set -eux; \
  apt-get update -qq; \
  curl -fsSL https://deb.nodesource.com/setup_16.x | bash -; \
  apt-get install -y nodejs; \
  npm install --global yarn; \
  yarn global add mjml; \
  mjml --version