require 'rubygems'
require 'rubygems/package_task'

SPEC = Gem::Specification.load 'mail.gemspec'

Gem::PackageTask.new(SPEC) { }

desc "Install the mail gem"
task :install => [:gem, :install_runtime_dependencies] do
  require 'rubygems/installer'
  Gem::Installer.new("pkg/#{SPEC.file_name}").install
end

desc "Install runtime dependencies"
task :install_runtime_dependencies do
  require 'rubygems/dependency_installer'
  SPEC.runtime_dependencies.each do |dep|
    puts "Installing #{dep.name} (#{dep.requirement})"
    Gem::DependencyInstaller.new.install(dep.name, dep.requirement)
  end
end
