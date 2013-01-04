require 'yaml'

desc 'Create a new post'
task :post do
  title = ENV.fetch('title') { 'New Post' }

  slug = title.downcase.gsub(/[^[:alnum:]]+/, '-')
  date = Date.today.strftime('%Y-%m-%d')

  path = "_posts/#{date}-#{slug}.markdown"

  if File.exist?(path)
    puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |file|
      file.puts YAML.dump({'layout' => 'post', 'category' => 'posts', 'title' => title})
      file.puts "---"
    end
  end

  exec 'vi', path
end
