module Ametista
  module Crono

    def timeout(sec, &block)
      sleep sec
      block.call
    end

    def hooked_timeout(sec, sec_proc, &block)
      i = sec
      while i > 0
        sec_proc.call i
        sleep 1
        i -= 1
      end
      block.call
    end

    @@threads = []

    def threaded(&block)
      @@threads << Thread.new(&block)
    end

  end
end
