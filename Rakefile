directory 'vendor'

file 'vendor/crystal.cson' => 'vendor' do |t|
  sh %[curl "https://raw.githubusercontent.com/atom-crystal/language-crystal/master/grammars/crystal.cson" > "#{t.name}"]
end

file 'vendor/crystal.json' => 'vendor/crystal.cson' do |t|
  sh %[cson2json #{t.source} > #{t.name}]
end

file 'Syntaxes/Crystal.tmLanguage' => 'vendor/crystal.json' do |t|
  sh "plutil -convert xml1 -o #{t.name} #{File.expand_path(t.source, Dir.pwd)}"
end

task :default => ['Syntaxes/Crystal.tmLanguage']