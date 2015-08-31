require 'ametista/config'
require 'ametista/logger'

module Ametista
  module Bifrost

    include Logger

    GIT_SHORTCUTS = {
      :co  => :checkout,
      :cm  => :commit,
      :b   => :branch, 
      :l   => :log,
      :r   => :reset, 
      :rb  => :rebase
    }

    def self.git_generate_shortcuts
      exec GIT_SHORTCUTS.map { |shct, cmd| "git config --global alias.#{shct} #{cmd}" }
    end

    def self.git_generate_user(name, email)
      exec [] << "git config --global user.name #{name}" << "git config --global user.email #{email}"
    end

    def self.exec(cmd, params = {})
      cmd = [ cmd ] if cmd.is_a? String
      cmd.map do |c|
        `#{c}`
        logger.debug "#{c}"
      end
    end
  end
end
