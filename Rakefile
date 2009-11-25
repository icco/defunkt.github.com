task :default => :build

desc "Build my site, dammit!"
task :build => [ :projects, :contact ]

def build(page)
  yaml = YAML.load_file("_pages/#{page}.yml")
  yaml["width"] = yaml[page.to_s].size * ((yaml['block-width'] || 260) + 32) + 4
  File.open("_pages/#{page}.yml", "w") { |f| f.puts yaml.to_yaml + "---\n" }
  system "cat _pages/#{page}.yml _pages/#{page}.mustache | mustache > #{page}.html"
end

task :projects do
  build :projects
end

task :contact do
  build :contact
end