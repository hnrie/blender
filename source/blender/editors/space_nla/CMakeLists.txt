# SPDX-FileCopyrightText: 2023 Blender Authors
#
# SPDX-License-Identifier: GPL-2.0-or-later

set(INC
  ../include
  ../../blenkernel
  ../../blenloader
  ../../blentranslation
  ../../gpu
  ../../makesrna
  ../../windowmanager

  # RNA_prototypes.hh
  ${CMAKE_BINARY_DIR}/source/blender/makesrna
)

set(INC_SYS
)

set(SRC
  nla_buttons.cc
  nla_draw.cc
  nla_edit.cc
  nla_ops.cc
  nla_select.cc
  nla_tracks.cc
  space_nla.cc

  nla_intern.hh
)

set(LIB
  bf_blenkernel
  PRIVATE bf::animrig
  PRIVATE bf::blenlib
  PRIVATE bf::depsgraph
  PRIVATE bf::dna
  PRIVATE bf::intern::guardedalloc
)

blender_add_lib(bf_editor_space_nla "${SRC}" "${INC}" "${INC_SYS}" "${LIB}")

# RNA_prototypes.hh dna_type_offsets.h
add_dependencies(bf_editor_space_nla bf_rna)
