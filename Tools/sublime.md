- install sublime
    $ sudo add-apt-repository ppa:webupd8team/sublime-text-3  
    $ sudo apt-get update  
    $ sudo apt-get install sublime-text-installer  

- install sublime package control
    #see https://packagecontrol.io/installation
    import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by) 


- sublime 不能输入中文的解决方法
    $ git clone https://github.com/lyfeyaj/sublime-text-imfix.git
    $ cd sublime-text-imfix
    $ ./sublime-imfix
    
- key blinding
	[
	    {"keys": ["ctrl+r"],
	     "caption": "SublimeREPL: Python - RUN current file",
	     "command": "run_existing_window_command", "args":
	     {"id": "repl_python_run", "file": "config/Python/Main.sublime-menu"}
	     },

	    {"keys": ["f5"],
	        "caption": "SublimeREPL: Python - IPython",
	        "command": "run_existing_window_command", "args":
	        {
	            "id": "repl_python_ipython",
	            "file": "config/Python/Main.sublime-menu"
	          }
	    },

	    { "keys": ["ctrl+m"], 
	        "command": "markdown_preview", 
	        "args": { "target": "browser"} 
	    }

	]

- 自动换行
	#add to User Setting
	"word_wrap" : true
