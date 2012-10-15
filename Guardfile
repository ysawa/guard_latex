guard :shell do
  watch /^([^\/]*)\.tex/ do |m|
    begin
      # make .dvi from .tex
      unless system("platex -halt-on-error #{m[0]}")
        raise
      end
      unless system("platex -halt-on-error #{m[0]}")
        raise
      end

      # make .pdf from .dvi
      unless system("dvipdfmx #{m[1]}.dvi")
        raise
      end
      system("rm #{m[1]}.dvi")
      system("rm #{m[1]}.aux")
      n "#{m[0]} is successfully compiled into pdf!", 'LaTeX compiling'
    rescue
      n "#{m[0]} failed to be compiled into pdf", 'LaTeX compiling', :failed
    end
  end
end
