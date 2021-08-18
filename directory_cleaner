import os
import shutil
import glob


# change to any directory
sort_dir = 'C:/Downloads'

file_extentions = {
    'unsorted': ('NULL'),
    'TEXT': ('.txt'),
    'OSU': ('.osk', '.osz', '.osr'),
    'DOCS': ('.docx', '.doc', '.pptx', '.ppt', '.xls', '.pdf'),
    'AUDIO': ('.mp3', '.flac', '.wav', '.ogg'),
    'IMAGES': ('.jpeg', '.jpg', '.png', '.gif', '.svg'),
    'INSTALLERS': ('.win', '.msi'),
    'SCRIPTS': ('.vbs', '.py', '.pyw', '.js'),
    'WEB': ('.html', '.css', '.htm'),
    'EXE': ('.exe', '.bat'),
    'ADOBE': ('.aep', '.psd', '.ffx'),
    'ZIP': ('.zip', '.rar', '.7z', '.bz2', '.xz', '.gz'),
    'VIDEO': ('.mp4', '.mov', '.avi', 'm4v', '.webm'),
}

# add exclusions from sorting
exclude = []

# WARNING: if true ALL subdirectories/files will be processed
is_recursive = False


def ext(file):
    ext = os.path.splitext(file)[-1]
    return ext


if is_recursive:
    wildcard = '/**/*.*'
else:
    wildcard = '/**'

for i in file_extentions:
    exclude.append(i.lower())

for file in glob.iglob(sort_dir + wildcard, recursive=is_recursive):
    file_name = os.path.basename(file)

    for extention_type in file_extentions:
        dest = extention_type.lower()

        if ext(file_name) in file_extentions[extention_type]:
            move_dest = f'{sort_dir}/{extention_type.lower()}/{file_name}'

        if not os.path.isdir(f'{sort_dir}/{dest}'):
            os.mkdir(f'{sort_dir}/{dest}')

        if os.path.isdir(file):
            if not is_recursive:
                move_dest = f'{sort_dir}/unsorted/'

    if file_name not in exclude and file_name != os.path.basename(__file__):
        try:
            shutil.move(file, move_dest)
            print(f'Moving {file} to {move_dest}\n')
            
        except NameError:
            print(f'Skipping {file}\n')
            continue
