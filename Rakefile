EDITOR = "${VISUAL:-${EDITOR:-vi}}"

desc "Start a new post"
task :new, :title do |t, args|
 args.with_defaults(:title => 'My New Post')
 title = args.title
 safe_title = title.downcase.gsub(/&/,'and').gsub(/[,'":\?!\(\)\[\]]/,'').gsub(/[\W\.]/, '-').gsub(/-+$/,'')
 filename = "_posts/#{Time.now.strftime('%Y-%m-%d')}-#{safe_title}.md"
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "date: #{Time.now.strftime('%Y-%m-%d')}"
    post.puts "permalink: /#{safe_title}.html"
    post.puts "---"
  end
  at_exit { exec "#{EDITOR} #{filename}" }
end
