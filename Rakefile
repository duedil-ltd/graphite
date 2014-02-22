# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'bundler/setup'

namespace :style do
  require 'rubocop/rake_task'
  desc 'Run rubocop for Ruby style checks'
  Rubocop::RakeTask.new(:ruby)
end

desc 'Run all style checks'
task style: ['style:chef', 'style:ruby']

require 'rspec/core/rake_task'
desc 'Run ChefSpec unit tests'
RSpec::Core::RakeTask.new(:unit) do |t|
  t.rspec_opts = "--color --format progress"
end

require 'kitchen'
desc 'Run Test Kitchen integration tests'
task :integration do
  Kitchen.logger = Kitchen.default_file_logger
  Kitchen::Config.new.instances.each do |instance|
    instances.test(:always)
  end
end

require 'emeril/rake'

