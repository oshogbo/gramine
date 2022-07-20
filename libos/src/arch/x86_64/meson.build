libos_asm_offsets_nasm = custom_target('asm-offsets.nasm[libos]',
    command: [libos_generated_offsets_print, '--n'],
    capture: true,
    output: 'asm-offsets.nasm',
)

libos_sources_arch_list = {
    'fs_proc/info.c': {},
    'libos_arch_prctl.c': {},
    'libos_context.c': {},
    'libos_elf_entry.nasm': { 'type': 'nasm' },
    'libos_table.c': {},
    'start.S': {},
    'syscallas.nasm': {
        'extra_files': [libos_asm_offsets_nasm],
        'type': 'nasm',
        'extra_args': ['-I', '@0@/'.format(meson.current_build_dir())],
    },
}

libos_sources_arch = files()

foreach src, params : libos_sources_arch_list
    if params.get('type', '') == 'nasm'
        libos_sources_arch += nasm_gen.process(
            [src] + params.get('extra_files', []),
            extra_args: params.get('extra_args', ''),
        )
    else
        libos_sources_arch += files(src)
    endif
endforeach

libos_lds = join_paths(meson.current_source_dir(), 'libos.lds')
