# configuration for rsync deployment
ssh_user = "ecruby@ecruby.org" # for rsync deployment
remote_root = "/home/ecruby/rubycamp.ecruby.org" # for rsync deployment

task :default => [:build]

desc "Build the site from HAML and SASS"
task :build do
  run "haml index.haml index.html --format=html5"
  run "mkdir styles"
  run "sass stylesheet.sass styles/stylesheet.css"
end

namespace :open do
  browsers = ["Google Chrome", "Mozilla Firefox", "Safari"].each do |browser|
    friendly_browser = browser.downcase.gsub(/\s/, "_").to_sym
    
    desc "Open the site with #{browser}"
    task friendly_browser do
      run "open ./index.html -a '#{browser}'"
    end
  end
  
  multitask :all => browsers.collect{|b| ("open:" + b.downcase.gsub(/\s/, "_")).to_sym}
end

def run (cmd)
  puts cmd
  `#{cmd}`
end

task :deploy => :build do
  puts "Deploying to #{remote_root}"
  system "rsync -avz --delete . #{ssh_user}:#{remote_root}"
end
