# Copyright © 2019 Google, Inc

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

xml_files = [
  'a2xx.xml',
  'a3xx.xml',
  'a4xx.xml',
  'a5xx.xml',
  'a6xx.xml',
  'adreno_common.xml',
  'adreno_pm4.xml',
]

freedreno_xml_header_files = []
foreach f : xml_files
  _name = f + '.h'
  freedreno_xml_header_files += custom_target(
    _name,
    input : ['gen_header.py', f],
    output : _name,
    command : [prog_python, '@INPUT@'],
    capture : true,
  )
endforeach

freedreno_xml_header_files += custom_target(
    'a6xx-pack.xml.h',
    input : ['gen_header.py', 'a6xx.xml'],
    output : 'a6xx-pack.xml.h',
    command : [prog_python, '@INPUT@', '--pack-structs'],
    capture : true,
  )
freedreno_xml_header_files += custom_target(
    'adreno-pm4-pack.xml.h',
     input : ['gen_header.py', 'adreno_pm4.xml'],
     output : 'adreno-pm4-pack.xml.h',
     command : [prog_python, '@INPUT@', '--pack-structs'],
     capture : true,
  )
