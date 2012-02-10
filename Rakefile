require 'rake'

desc 'Install dotfiles'
task :install => ['vim:update_submodules'] do
  symlinks = [
    {:source => 'ack/ackrc', :target => '.ackrc'},
    {:source => 'vim', :target => '.vim'},
    {:source => 'vim/vimrc', :target => '.vimrc'},
    {:source => 'git/gitconfig', :target => '.gitconfig'}
  ]

  symlinks.each do |symlink|
    source = symlink[:source]
    target = "#{ENV["HOME"]}/#{symlink[:target]}"

    if File.exists?(target)
      `mv "#{target}" "#{target}.backup"`
    end

    `ln -s "$PWD/#{source}" "#{target}"`
  end
end

desc 'Uninstall dotfiles'
task :uninstall do
end

namespace :vim do
  desc 'Update submodules'
  task :update_submodules do
    `git submodule init`
    `git submodule update`
  end
end

task :default => :install
