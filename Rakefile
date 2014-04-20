task :default => [:deploy]

task :build do
	puts "-----generate Jekyll build"
	#build the site
	system("jekyll build")
	puts "-----build done"
	puts ""
end

task :deploy => :build do
	#push to server
	HOST = "192.168.1.254"
	USER = "matthew"
	REMOTE = "/var/www/archive.digivation.net/"
	LOCAL = "#{Dir.pwd}/_site/"

	puts "-----Deploying"
	system("rsync -avz --delete #{LOCAL} #{USER}@#{HOST}:#{REMOTE}")
end
