module Ametista
  module ModuleConvention

    def self.included(klass)

      Object.class_eval do
            
        def modules_init(params = {})
          self.singleton_class.included_modules.reject {|m| m == Kernel || m == Ametista::ModuleConvention }.map do |m|
            meth = "_init_#{m}"
            self.send(meth, params) if self.respond_to? meth
          end
        end

      end

    end

  end
end