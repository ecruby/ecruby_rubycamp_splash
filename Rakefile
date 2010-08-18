# configuration for rsync deployment
ssh_user = "ecrubycamp@rubycamp.ecruby.org" # for rsync deployment
remote_root = "/home/ecrubycamp/rubycamp.ecruby.org" # for rsync deployment

task :default => [:build]

desc "Build the site from HAML and SASS"
task :build do
  run "haml index.haml index.html --format=html5"
  run "mkdir styles"
  run "sass stylesheet.sass styles/stylesheet.css"
end

def run (cmd)
  puts cmd
  `#{cmd}`
end

task :deploy do
  puts "Deploying to #{remote_root}"
  system "rsync -avz --delete . #{ssh_user}:#{remote_root}"
end
