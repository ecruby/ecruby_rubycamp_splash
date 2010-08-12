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