# Use the official Ruby image.
# https://hub.docker.com/_/ruby
FROM ruby:3.4

# Install production dependencies.
WORKDIR /usr/src/app

# Copia os arquivos de dependência do Ruby
COPY Gemfile Gemfile.lock ./

ENV BUNDLE_FROZEN=true

# Instala o Bundler e configura para não incluir 'test' no bundle
RUN gem install bundler && bundle config set --local without 'test'

# Copia o código local para a imagem do contêiner.
COPY . ./

# Instala as gems (dependências)
RUN bundle install

# Executa o serviço web na inicialização do contêiner.
CMD ["ruby", "./app.rb"]