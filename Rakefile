
namespace :relish do
  desc "Push docs to production"
  task :prod do
    sh "relish push:publisher rspec"
  end

  desc "Push docs to staging for viewing"
  task :staging do
    sh "relish push:publisher rspec-staging"
  end
end
