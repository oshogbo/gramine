includes_libos = [
    include_directories(
        '.',
        'arch/@0@'.format(host_machine.cpu_family()),
    ),
    includes_pal_for_libos,
    common_inc,
]

libos_generated_offsets_print = executable('libos-generated-offsets-print',
    'generated_offsets.c',
    generated_offsets_print_src,
    include_directories: includes_libos,
    c_args: cflags_libos,
)
