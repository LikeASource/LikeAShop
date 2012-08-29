var hogan = require('hogan.js'),
    fs    = require('fs')

var rootDir      = __dirname
var sourcesDir   = rootDir + '/src/'

namespace('build', function() {
    task('css',  [], function() {
        
    })
    task('js',   [], function() {
        
    })
    task('html', [], function() {
        var layout, pages
        layout = fs.readFileSync(sourcesDir + 'templates/layout.mustache', 'utf-8')
        layout = hogan.compile(layout)
        fs.readdirSync(sourcesDir + 'templates/pages').forEach(function(name) {
            if (!name.match(/\.mustache$/)) return
            var page  = fs.readFileSync(sourcesDir + 'templates/pages/' + name, 'utf-8'),
                title = name.replace(/\.mustache/, '')
                            .replace(/\-.*/, '')
                            .replace(/(.)/, function ($1) { return $1.toUpperCase() })
            page     = hogan.compile(page)
            page     = layout.render({title: title, yield: page})
            fs.writeFileSync(rootDir + '/' + name.replace(/mustache$/, 'html'), page, 'utf-8')
        })
    })
    task('all',  ['build:css', 'build:js', 'build:html'], function() {
        
    })    
})

task('default', function() {

})
