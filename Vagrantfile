#!/usr/bin/env ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
ENV['PATH'] = '/opt/chefdk/bin:/usr/local/bin:/usr/bin:%s' % ENV['PATH']

Vagrant.configure('2') do |config|
  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true

  config.vm.define 'vagrant' do |node|
    node.vm.box = 'bento/ubuntu-14.04'
    node.vm.hostname = 'vagrant'
    node.vm.provision :chef_solo do |chef|
      chef.log_level = :info
      chef.json = {}
      chef.run_list = %w(
        recipe[apt]
        recipe[sai_nrpe]
        recipe[minitest-handler]
      )
    end
  end
end