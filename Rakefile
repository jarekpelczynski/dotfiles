desc "Copy dotfiles to you home directory"
task :install  do
	overwrite_all = false

	files = Dir.glob('*/**')
	files.each do |path|
		file = path.split('/').last
		target = "#{ENV["HOME"]}/.#{file}"

		if File.exists?(target)
			overwrite = false

			unless overwrite || overwrite_all
				puts "THe file '.#{file}' already exist. Overwrite this file? [y]es / [n]o / overwite [all]"
				case STDIN.gets.chomp
					when 'y' then overwrite = true
					when 'n' then overwrite = false
					when 'all' then overwrite_all = true
				end
			end
		end

		`cp "$PWD/#{path}" "#{target}"`
	end
end

task :default => ["install"]