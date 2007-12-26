require "rake"
require "rake/clean"
require "rake/gempackagetask"
require "rake/rdoctask"
require "fileutils"

include FileUtils

PROJECTS = %w{core model}

def with_each_project
  PROJECTS.each do |p|
    FileUtils.cd(p)
    begin
      yield p
    ensure
      FileUtils.cd('..')
    end
  end
end

def sh_with_each_project(cmd)
  with_each_project {sh cmd rescue nil}
end

desc "Packages up Sequel and Sequel Model."
task :default => [:package]
task :package => [:clean]
task :doc => [:rdoc]

task :package do
  sh_with_each_project "rake package"
end

task :install do
  sh_with_each_project "rake install"
end

task :install_no_docs do
  sh_with_each_project "rake install_no_docs"
end

task :uninstall => [:clean] do
  sh_with_each_project "rake uninstall"
end

task :spec do
  sh_with_each_project "rake spec"
end

task :spec_no_cov do
  sh_with_each_project "rake spec_no_cov"
end
