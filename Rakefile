# encoding: utf-8

require 'rubygems'
require 'bundler'
require 'cover_me'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "emoji_palette"
  gem.homepage = "http://github.com/mshibuya/emoji_palette"
  gem.license = "GPL"
  gem.summary = %Q{PC emoji translation support for jpmobile using TypePad emoji icons}
  gem.description = %Q{PC emoji translation support for jpmobile using TypePad emoji icons}
  gem.email = "mit.shibuya@gmail.com"
  gem.authors = ["Mitsuhiro Shibuya"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new

require 'rspec/core'
require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec) do |spec|
  spec.pattern = FileList['spec/**/*_spec.rb']
end

RSpec::Core::RakeTask.new(:rcov) do |spec|
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :default => :spec

require 'rdoc/task'
RDoc::Task.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "emoji_palette #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

CoverMe.config do |c|
  c.at_exit = Proc.new {}
  c.file_pattern = /#{c.project.root}\/lib\/.+\.rb/ix
end

namespace :cover_me do
  task :report do
    CoverMe.complete!
  end
end

task :test do
  Rake::Task['cover_me:report'].invoke
end

task :spec do
  Rake::Task['cover_me:report'].invoke
end

