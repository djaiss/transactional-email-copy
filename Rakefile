# Highly inspired by Octopress

## -- Rsync Deploy config -- ##
# Be sure your public key is listed in your server's ~/.ssh/authorized_keys file
ssh_user        = "djaiss@djaiss.webfactional.com"
document_source = "~/htdocs/transactionalemailcopy/_site/"
document_root   = "/home/djaiss/webapps/transactionalemailcopy/"
rsync_delete    = true


#######################
# Working with Jekyll #
#######################

desc "Generate jekyll site"
task :generate do
  puts "## Generating Site with Jekyll"
  system "jekyll"
end

desc "Run the jekyll server"
task :run do
  puts "## Running Site with Jekyll"
  system "jekyll --server"
end

desc "Create a new sample post"
task :new_post do
  return print "You need to specify COMPANY environment variable as follow: rake new_post COMPANY=trello\n" unless ENV['COMPANY']

  company_name = ENV["COMPANY"].downcase
  time = Time.new
  time_string = time.year.to_s + "-" + time.strftime("%m") + "-" + time.strftime("%d")
  filename = time_string + "-" + company_name + ".md"
  
  #Generate the document
  doc = <<END 
---
layout: post
title: #{company_name.capitalize} Account Confirmation
image: #{time_string}-#{company_name}.png
companyurl: 
company: #{company_name.capitalize}
category: welcome-email
category-fullname: Welcome email
dateposted: #{time_string} 
author: #{`git config user.name`.gsub(/\s+/, "")} 
author-url: http://djaiss.github.com
subject: 
---
END
  File.open('_posts/' + filename, 'w') {|f| f.write(doc) }
end

##############
# Deploying  #
##############

desc "Default deploy task"
task :deploy do
  puts "## About to deploy to production"
  puts ""
  puts "## Generating the site"
  Rake::Task[:generate].execute
  puts "## Rsync in progress"
  system "rsync -arvuz --delete #{document_source} #{ssh_user}:#{document_root} --chmod=ugo=rwX --exclude '.git'"
  puts "## Rsync complete. The website is up-to-date."
end

desc "Purge the cache on Cloudflare"
task :purge do
  puts "## Reading API KEY from the .cloudflare_api_key file"
  cloudflare_api_key = IO.read(".cloudflare_api_key").gsub(/\s+/, "")

  puts "## Purging Cloudflare's cache"
  system "curl https://www.cloudflare.com/api_json.html -d 'a=fpurge_ts' -d 'tkn=#{cloudflare_api_key}' -d 'email=cloudflarerfr@fastmail.fm' -d 'z=totalwireframe.com' -d 'v=1'"
  puts "## Purging done"
end

desc "list tasks"
task :list do
  puts "Tasks: #{(Rake::Task.tasks - [Rake::Task[:list]]).join(', ')}"
  puts "(type rake -T for more detail)\n\n"
end
