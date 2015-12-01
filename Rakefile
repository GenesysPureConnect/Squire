task :default => ["build/squire.js"]

SRC = ["source/intro.js", "source/Constants.js", "source/TreeWalker.js", "source/Node.js", "source/Range.js", "source/KeyHandlers.js", "source/Clean.js", "source/Clipboard.js", "source/Editor.js", "source/outro.js"]

task :concatenate_js => SRC do
    out = ""
    SRC.each do |file|
        out += File.read(file).gsub(/^\/\*jshint(.*)\n/, '')
    end

    File.open("build/squire-raw.js", 'w') { |file|
        file.write(out)
    }

    puts "concatenated squire-raw.js"
end

file "build/squire.js" => :concatenate_js do
    sh "uglifyjs build/squire-raw.js -c -m -o build/squire.js"
end