
fs = require('fs')
path = require('path')
exec = require('child_process').exec

less_dir = "views/less"
less_srcs = [ "index.less", "resume2.less" ]
styles_dir = "static/styles"

option '-x', '--compress', 'compress compiled code'

task 'css', 'build css from less bootstrap', (options) ->
  fs.mkdir styles_dir
  for src in less_srcs
    fname = path.basename src, '.less'
    command = "lessc #{less_dir}/#{src} > #{styles_dir}/#{fname}.css"
    console.info command
    exec command, (err, stdo, stde) ->
      console.error err, stde, stdo if err != null
    if options.compress
      command = "lessc --compress #{less_dir}/#{src} > #{styles_dir}/#{fname}.min.css"
      console.info command
      exec command, (err, stdo, stde) ->
        console.error err, stde, stdo if err != null
