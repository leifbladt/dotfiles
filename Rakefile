require 'rake'

desc 'Install dotfiles'
task :install do
  symlinks = [
    {:source => 'ack/ackrc', :target => '.ackrc'},
    {:source => 'vim', :target => '.vim'},
    {:source => 'vim/vimrc', :target => '.vimrc'},
    {:source => 'git/gitconfig', :target => '.gitconfig'},
    {:source => 'git_template', :target => '.git_template'},
    {:source => 'zsh/zshenv', :target => '.zshenv'},
    {:source => 'zsh/zshrc', :target => '.zshrc'}
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

task :default => :install
