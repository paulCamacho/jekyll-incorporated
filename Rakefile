require "rubygems"
require "tmpdir"

require "bundler/setup"
require "jekyll"


# Change your GitHub reponame eg. "kippt/jekyll-incorporated"
GITHUB_REPONAME = ""


namespace :site do
  desc "Generate blog files"
  task :generate do
    Jekyll::Site.new(Jekyll.configuration({
      "source"      => ".",
      "destination" => "_site"
    })).process
  end


  # Commented out the Github publish so we don't accidentally do that...
  #
  # desc "Generate and publish blog to gh-pages"
  # task :publish => [:generate] do
  #   Dir.mktmpdir do |tmp|
  #     cp_r "_site/.", tmp
  #     Dir.chdir tmp
  #     system "git init"
  #     system "git add ."
  #     message = "Site updated at #{Time.now.utc}"
  #     system "git commit -m #{message.inspect}"
  #     system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
  #     system "git push origin master:refs/heads/gh-pages --force"
  #   end
  # end

  desc 'Deploy to fizzyinc.com via rsync'
  task :deploy => [:generate] do
    # uploads ALL files as we often do site-wide changes and prefer overwriting all
    puts 'DEPLOYING TO FIZZYINC.COM'
    sh "rsync -rtzh --progress --delete _site/ fizzyinc@fizzyinc.com:~/public_html/blog/"
    puts 'done!'
  end
end
