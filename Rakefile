task :deploy do
  system 'jekyll build && s3cmd sync --delete-removed --acl-public --reduced-redundancy --cf-invalidate _site/ s3://davestagner.com/ --verbose'
end