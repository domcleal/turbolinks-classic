require 'rake/testtask'

Rake::TestTask.new do |t|
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.warning = true
  t.verbose = true
end

namespace :test do
  task :all do
    rails_versions = []
    rails_versions.push('rails32', 'rails40', 'rails41') if RUBY_VERSION < '2.4'
    rails_versions.push('rails42', 'rails50')
    rails_versions.each do |gemfile|
      sh "BUNDLE_GEMFILE='Gemfile.#{gemfile}' bundle --quiet"
      sh "BUNDLE_GEMFILE='Gemfile.#{gemfile}' bundle exec rake test"
    end
  end
end
