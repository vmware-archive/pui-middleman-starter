desc "Build the website from source"
task :build do
 puts "## Building website"
 status = system("middleman build")
 puts status ? "OK" : "FAILED"
end

desc "Deploy site to PWS"
task :pws_deploy => :build do
 system("git push")
 system("touch build/Staticfile")
 system("cf target -o PCF-Design -s pui")
 system("cf zero-downtime-push pui-middleman-starter -f manifest.yml -p ./build")
end
