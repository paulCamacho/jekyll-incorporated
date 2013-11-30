require "rubygems"

require "bundler/setup"
require "jekyll"


namespace :site do

  desc "Build site in development mode"
  task :devbuild do
    puts "Nuking the existing site"
    sh 'rm -rf _site'
    puts "Building with a development configuration."
    sh 'jekyll build --trace --config _development_config.yml,_config.yml'
  end

  desc "Build site in production mode"
  task :probuild do
    puts "Nuking the existing site"
    sh 'rm -rf _site'
    puts "Building with a production configuration."
    sh 'jekyll build --trace --config _production_config.yml,_config.yml'
  end

  desc "Serve in development mode"
  task :serve do
    puts "Serving with a development configuration."
    sh 'jekyll serve --config _development_config.yml,_config.yml'
  end

  desc "Serve and watch in development mode"
  task :watch do
    puts "Serving and watching (auto-regenerating) with a development configuration."
    sh 'jekyll serve --watch --config _development_config.yml,_config.yml'
  end

  desc 'Deploy to fizzyinc.com via rsync'
  task :deploy do
    # uploads ALL files as we often do site-wide changes and prefer overwriting all
    puts 'Deploying to fizzyinc.com'
    sh "rsync -rtzh --progress --delete _site/ fizzyinc@fizzyinc.com:~/public_html/"
    puts 'done!'
  end
end

