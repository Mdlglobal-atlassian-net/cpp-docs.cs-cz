---
title: ARM – vnitřní funkce
description: Referenční seznam vnitřních částí ARM64 podporovanýkompilátorem Microsoft C++ v sadě Visual Studio.
ms.date: 09/02/2019
f1_keywords:
- arm_neon/vsetq_lane_p8
- armintr/_arm_uxtb
- arm_neon/vld4_lane_p8
- arm_neon/vrshrn_n_s64
- arm_neon/vsli_n_u32
- arm_neon/vsraq_n_u16
- arm_neon/vcgt_f32
- armintr/__iso_volatile_store32
- arm_neon/vceqq_f32
- armintr/_arm_smlal
- arm_neon/vmull_n_s32
- arm_neon/vmax_s8
- arm_neon/vmvn_u32
- arm_neon/vrshl_u32
- arm_neon/int32x2_t
- arm_neon/vdupq_n_p8
- arm_neon/vpmax_u16
- arm_neon/vtrnq_s32
- arm_neon/vset_lane_f32
- arm_neon/vrev64_s8
- arm_neon/vtrnq_p8
- arm_neon/vqshlq_u64
- arm_neon/vld1q_dup_s64
- arm_neon/vmovq_n_u64
- arm_neon/vqshrn_n_u16
- arm_neon/vhadd_s32
- arm_neon/vrhaddq_u32
- arm_neon/vst1q_p8
- arm_neon/vshrn_n_s16
- arm_neon/vget_high_f32
- arm_neon/vuzpq_s16
- arm_neon/vand_u16
- arm_neon/vmulq_s32
- arm_neon/vrsraq_n_s64
- arm_neon/vceqq_s8
- arm_neon/uint64x1x3_t
- arm_neon/veor_u32
- armintr/_arm_pkhtb
- arm_neon/vorrq_u16
- arm_neon/vpaddl_s8
- arm_neon/vmla_n_s16
- arm_neon/vqdmlal_lane_s32
- arm_neon/vshlq_n_u8
- arm_neon/vst2_lane_p8
- arm_neon/vld3q_u16
- arm_neon/vandq_u8
- arm_neon/vst1_u64
- arm_neon/vaddq_s64
- arm_neon/vuzpq_u32
- arm_neon/vld3_lane_p8
- arm_neon/vminq_s32
- arm_neon/vabd_u16
- arm_neon/vdup_n_u32
- arm_neon/vmul_p8
- arm_neon/vsra_n_u16
- arm_neon/vst3q_u16
- arm_neon/int32x2x3_t
- arm_neon/vld2_dup_u16
- arm_neon/vrhaddq_u8
- arm_neon/vhadd_u8
- arm_neon/vgetq_lane_s32
- arm_neon/vcleq_u16
- arm_neon/vabdq_s8
- arm_neon/vrev16q_u8
- arm_neon/vqshlu_n_s64
- arm_neon/vcvt_n_s32_f32
- arm_neon/vqrshrn_n_s64
- arm_neon/vst1q_p16
- arm_neon/vgetq_lane_s16
- arm_neon/vtstq_u32
- arm_neon/vmlsl_n_s16
- arm_neon/vcge_s8
- arm_neon/vshr_n_s16
- armintr/_arm_rbit
- arm_neon/vmls_u32
- arm_neon/vmls_lane_u32
- arm_neon/vcvtq_n_s32_f32
- arm_neon/vqshl_n_s8
- arm_neon/vst1q_s16
- armintr/__emit
- arm_neon/vshlq_s64
- arm_neon/vuzp_s8
- arm_neon/vld1q_lane_s64
- arm_neon/veorq_s32
- arm_neon/vaddq_u64
- arm_neon/vceq_s32
- arm_neon/vmovn_u16
- arm_neon/vabal_s8
- arm_neon/vabsq_f32
- armintr/_arm_smuad
- arm_neon/veor_u8
- arm_neon/int16x4_t
- arm_neon/vsraq_n_s16
- arm_neon/vshlq_s8
- arm_neon/vcreate_u32
- arm_neon/vzipq_s8
- arm_neon/vst3q_u8
- arm_neon/int64x1x4_t
- armintr/__iso_volatile_store16
- arm_neon/vst4_lane_p16
- arm_neon/vld1_dup_p16
- arm_neon/vhadd_s16
- arm_neon/vtbl2_s8
- arm_neon/veorq_u32
- arm_neon/vqdmlal_lane_s16
- arm_neon/vrsra_n_u8
- arm_neon/vbslq_u16
- arm_neon/vget_low_s64
- arm_neon/vceq_u16
- arm_neon/vdupq_lane_u32
- arm_neon/vabdl_u32
- arm_neon/vmlal_s32
- arm_neon/vst1_lane_u8
- arm_neon/vld4q_f16
- arm_neon/vqdmlsl_s32
- arm_neon/vqrdmulh_s32
- arm_neon/vqrshl_u8
- arm_neon/uint32x4x4_t
- arm_neon/vabaq_u16
- arm_neon/vcnt_p8
- arm_neon/vld3q_s16
- arm_neon/vshl_n_u32
- arm_neon/vrev64q_u16
- arm_neon/vextq_s64
- arm_neon/vhsubq_s8
- arm_neon/vld2_dup_u8
- arm_neon/vst3_s16
- arm_neon/vorn_u16
- arm_neon/vst4_f16
- arm_neon/vpadalq_u8
- armintr/__iso_volatile_load8
- arm_neon/vmovl_u16
- arm_neon/vld4q_u32
- arm_neon/vcgt_u32
- arm_neon/vmlaq_n_u32
- arm_neon/vrsra_n_u64
- arm_neon/vst4_s8
- arm_neon/vcvtq_n_f32_u32
- arm_neon/vst2q_u16
- arm_neon/vqshrn_n_s16
- arm_neon/vld4_s16
- arm_neon/uint16x8x4_t
- arm_neon/vrsqrte_u32
- arm_neon/vcltq_s8
- arm_neon/vst3_u16
- arm_neon/vst2_f32
- arm_neon/vld2_u64
- arm_neon/vst1_u16
- arm_neon/vmls_s16
- arm_neon/vqrshlq_s32
- arm_neon/vqdmull_s16
- arm_neon/vld2_lane_p16
- arm_neon/vpaddlq_u8
- arm_neon/vcvt_n_f32_u32
- arm_neon/vcgtq_u8
- arm_neon/vshl_s32
- arm_neon/vtbx3_p8
- arm_neon/vld3_dup_s32
- arm_neon/int16x4x3_t
- arm_neon/vcale_f32
- arm_neon/vqabsq_s32
- arm_neon/vmulq_u16
- arm_neon/vst1_s8
- arm_neon/vclt_u8
- armintr/_arm_sxtb16
- arm_neon/vshr_n_s8
- arm_neon/vst1_lane_f16
- arm_neon/vorn_s64
- armintr/_arm_usub8
- arm_neon/vst4_lane_f32
- arm_neon/vmls_lane_u16
- arm_neon/vpaddl_u32
- arm_neon/vdup_lane_u64
- arm_neon/vsri_n_p16
- arm_neon/vqrshlq_u64
- arm_neon/vclz_s16
- arm_neon/vsra_n_u32
- arm_neon/vabaq_s8
- arm_neon/vst2_lane_s8
- arm_neon/vcvt_n_u32_f32
- arm_neon/vst3_u32
- arm_neon/vcvtq_f32_u32
- arm_neon/vraddhn_s64
- armintr/_arm_uqsax
- arm_neon/vshl_u8
- armintr/_arm_uqadd16
- arm_neon/vrsra_n_u16
- arm_neon/vrshl_u64
- arm_neon/int32x4x3_t
- arm_neon/vmull_u8
- arm_neon/vcombine_u64
- arm_neon/vmull_u16
- arm_neon/vld1_dup_s8
- armintr/_CountLeadingSigns64
- arm_neon/vqshlq_n_s32
- arm_neon/vrecpe_f32
- arm_neon/vsri_n_u32
- arm_neon/vrsraq_n_s8
- arm_neon/vsetq_lane_s16
- arm_neon/vget_high_u32
- arm_neon/vmlal_u32
- arm_neon/vdupq_lane_s16
- arm_neon/vsubq_u64
- arm_neon/vext_p8
- arm_neon/vshl_u16
- arm_neon/vmls_n_u16
- arm_neon/vmull_s16
- arm_neon/vmovq_n_s64
- arm_neon/vaddq_f32
- arm_neon/vshl_n_s16
- arm_neon/vext_p16
- arm_neon/vextq_u32
- arm_neon/vld1_p8
- arm_neon/veor_s32
- arm_neon/int16x8x4_t
- arm_neon/vst1q_u16
- arm_neon/vzipq_p8
- arm_neon/int32x4x4_t
- arm_neon/vqdmulhq_lane_s32
- arm_neon/vst3_lane_u32
- arm_neon/vhsubq_s32
- armintr/__static_assert
- arm_neon/vst3q_lane_u16
- arm_neon/vpmin_u32
- arm_neon/vrev64q_p16
- arm_neon/vcleq_f32
- arm_neon/vhsub_u16
- arm_neon/vld2_lane_s32
- arm_neon/vmlsl_s32
- armintr/_arm_rev
- arm_neon/vcgeq_s16
- arm_neon/vmulq_s8
- arm_neon/vsri_n_s8
- arm_neon/vpadd_f32
- arm_neon/vld1q_lane_f16
- arm_neon/vmls_u16
- arm_neon/vld1_lane_f32
- arm_neon/vmlaq_lane_s16
- arm_neon/vqadd_u32
- arm_neon/vmul_n_s32
- arm_neon/vld1q_dup_p8
- arm_neon/vtrnq_s8
- arm_neon/vbslq_p8
- arm_neon/vget_lane_s8
- arm_neon/vext_u16
- arm_neon/vsubq_s16
- arm_neon/vld4_lane_s8
- arm_neon/uint32x2x2_t
- arm_neon/vdup_n_s8
- arm_neon/vld4_lane_u16
- arm_neon/vmovq_n_s16
- arm_neon/vst4q_s32
- arm_neon/vst2q_f16
- arm_neon/vbslq_s16
- arm_neon/vand_u64
- arm_neon/poly16_t
- arm_neon/vaba_u16
- arm_neon/vqshlq_s64
- armintr/_arm_uxth
- arm_neon/vst2_lane_s16
- arm_neon/vand_u8
- arm_neon/int8x16x3_t
- arm_neon/vrev64_u16
- arm_neon/vld2_lane_s16
- arm_neon/vabaq_s16
- arm_neon/vsli_n_u8
- arm_neon/vsraq_n_u64
- arm_neon/vmlsl_s16
- arm_neon/vmovn_u64
- arm_neon/vld4_f32
- arm_neon/vst2q_f32
- arm_neon/vtbx3_u8
- arm_neon/vcombine_s8
- arm_neon/vqdmulhq_s32
- arm_neon/vgetq_lane_p8
- armintr/_arm_smusd
- arm_neon/vpmax_u32
- arm_neon/vceq_f32
- arm_neon/vsri_n_p8
- arm_neon/vhsubq_u8
- arm_neon/vuzp_s16
- arm_neon/uint32x2x4_t
- arm_neon/vst4_lane_s32
- arm_neon/vsli_n_p8
- arm_neon/vld3_lane_f16
- arm_neon/vbic_u64
- arm_neon/vmlal_u16
- arm_neon/vmvn_s8
- arm_neon/vtstq_s8
- arm_neon/vmaxq_s32
- arm_neon/vqmovn_u64
- armintr/_arm_ssax
- arm_neon/vext_u32
- arm_neon/vld1_dup_u64
- arm_neon/vmlal_n_s16
- armintr/_arm_smulbb
- arm_neon/vqrdmulhq_lane_s16
- arm_neon/vdup_n_p8
- arm_neon/vaba_s8
- arm_neon/vrshrq_n_s32
- arm_neon/vmvnq_s32
- arm_neon/vpadal_s32
- arm_neon/vqshl_s16
- arm_neon/vtrn_p8
- arm_neon/vzip_s16
- arm_neon/vcge_f32
- armintr/_arm_sxtab16
- arm_neon/vst1q_lane_u64
- arm_neon/vqrshlq_u16
- arm_neon/int8x8_t
- arm_neon/vorr_u8
- arm_neon/vrev64_f32
- arm_neon/vpaddlq_s16
- arm_neon/vdupq_lane_u64
- arm_neon/vcltq_u16
- arm_neon/vst3_lane_f32
- arm_neon/vld2_dup_f32
- armintr/_arm_smmul
- arm_neon/vbsl_s16
- arm_neon/vld1_lane_u8
- arm_neon/vld2q_lane_u16
- arm_neon/vqshlu_n_s32
- armintr/_arm_smlalbt
- arm_neon/vmla_s8
- arm_neon/vsli_n_p16
- arm_neon/vmla_u8
- arm_neon/vqaddq_s16
- arm_neon/vld3_p16
- arm_neon/uint64x2x4_t
- arm_neon/vcnt_u8
- arm_neon/vcltq_u8
- arm_neon/vtbx1_p8
- arm_neon/vrev32q_u16
- arm_neon/vld1_lane_u16
- arm_neon/vqadd_s16
- arm_neon/vcnt_s8
- armintr/_MulUnsignedHigh
- arm_neon/vsliq_n_u8
- arm_neon/vpmin_s16
- armintr/__iso_volatile_load16
- arm_neon/vst2_lane_f32
- arm_neon/vqsubq_s32
- arm_neon/vqshl_s32
- arm_neon/vsraq_n_u32
- arm_neon/vcreate_s32
- arm_neon/vld3q_lane_u32
- arm_neon/vaddq_u16
- arm_neon/vand_s32
- arm_neon/vbicq_s32
- armintr/_arm_smulbt
- arm_neon/vrsra_n_s8
- arm_neon/vshrq_n_u32
- arm_neon/vld4_f16
- arm_neon/vcagtq_f32
- arm_neon/vaddw_u32
- armintr/_arm_uxtah
- arm_neon/vtstq_u8
- arm_neon/vld1_dup_u16
- arm_neon/int16x4x4_t
- arm_neon/vqshluq_n_s8
- arm_neon/vqdmulhq_n_s32
- arm_neon/vst1_s64
- arm_neon/vrsubhn_u16
- arm_neon/vld4_dup_p16
- arm_neon/vmlaq_s32
- arm_neon/vnegq_s32
- arm_neon/vst2q_u8
- arm_neon/vget_low_s32
- arm_neon/vorn_u32
- arm_neon/vld1q_s8
- arm_neon/vandq_s64
- arm_neon/vmvn_p8
- arm_neon/vabdl_s16
- arm_neon/vqshl_u32
- arm_neon/vld3_dup_u16
- arm_neon/vmov_n_f32
- arm_neon/vcvt_f32_u32
- arm_neon/vrhadd_s8
- arm_neon/vpadal_u32
- armintr/_arm_ubfx
- arm_neon/vcgt_s8
- arm_neon/vget_lane_f32
- arm_neon/vcge_s16
- arm_neon/vmov_n_s64
- arm_neon/vmulq_n_f32
- arm_neon/vpadalq_u32
- armintr/_arm_smlaldx
- arm_neon/vtst_u16
- arm_neon/vmls_n_s16
- arm_neon/vcombine_f32
- arm_neon/vld1q_p16
- armintr/_arm_ssat
- arm_neon/vextq_s8
- arm_neon/vmax_u32
- arm_neon/vqsubq_s64
- arm_neon/vcltq_s16
- arm_neon/vst2q_s8
- arm_neon/vpmax_u8
- arm_neon/vld4_dup_p8
- arm_neon/vrshr_n_u64
- arm_neon/vqrshrun_n_s16
- arm_neon/vget_low_u64
- arm_neon/vst2q_s32
- arm_neon/vst4_s32
- arm_neon/vrshrq_n_u8
- arm_neon/vdupq_n_u64
- arm_neon/vsriq_n_u8
- arm_neon/vdupq_lane_u8
- arm_neon/vsriq_n_s64
- arm_neon/vget_low_u8
- arm_neon/vst1_lane_p16
- arm_neon/vld1q_lane_u8
- arm_neon/vcgt_s32
- arm_neon/vst1_lane_u32
- arm_neon/vzipq_p16
- arm_neon/vmvn_u16
- arm_neon/vld1q_lane_u16
- armintr/_MoveToCoprocessor64
- arm_neon/vdup_n_u16
- arm_neon/vzipq_f32
- arm_neon/vshl_s16
- arm_neon/vmlaq_n_s16
- arm_neon/vget_lane_s64
- arm_neon/vld1q_lane_f32
- arm_neon/vnegq_s16
- armintr/_arm_usax
- arm_neon/vabd_s16
- arm_neon/vmovq_n_u32
- arm_neon/vshlq_n_u16
- armintr/_CountLeadingSigns
- arm_neon/vld3q_f16
- arm_neon/vceqq_u32
- arm_neon/int8x8x2_t
- arm_neon/vst2_s64
- arm_neon/vst4q_lane_s16
- arm_neon/vorn_s32
- arm_neon/vcle_f32
- arm_neon/vld1_p16
- arm_neon/vtrn_u32
- arm_neon/vbsl_s32
- arm_neon/float32x2_t
- arm_neon/vmvn_s32
- arm_neon/vqdmlsl_lane_s16
- arm_neon/vtbl3_s8
- arm_neon/vsra_n_u8
- arm_neon/vcvtq_u32_f32
- arm_neon/vst1_p8
- arm_neon/vrev64_p16
- armintr/__ldrexd
- arm_neon/vcgeq_u8
- arm_neon/vmlal_n_s32
- arm_neon/vst1q_lane_p8
- arm_neon/vpadalq_s32
- arm_neon/vtstq_p8
- arm_neon/vld4_lane_u8
- armintr/_arm_ssub16
- arm_neon/vpaddlq_u16
- armintr/_arm_udiv
- arm_neon/vld1_lane_p8
- arm_neon/vst1q_u32
- arm_neon/vld1_f32
- arm_neon/uint64x2x2_t
- arm_neon/vqsubq_u64
- arm_neon/vld4q_s32
- arm_neon/vceq_s16
- arm_neon/vst3_s64
- arm_neon/vext_s8
- armintr/_arm_smlsd
- arm_neon/vpadal_s16
- arm_neon/vbic_s32
- arm_neon/vld1_dup_u8
- arm_neon/vclt_f32
- arm_neon/vrev64_s16
- arm_neon/vrshlq_s64
- arm_neon/vdupq_n_s64
- arm_neon/vuzp_p16
- arm_neon/vld3_dup_p16
- arm_neon/vcreate_s8
- armintr/_arm_smlatt
- arm_neon/vtst_s32
- arm_neon/vshrq_n_s64
- arm_neon/vqshlq_n_s64
- arm_neon/vqshlu_n_s16
- arm_neon/vcleq_s16
- arm_neon/vmull_lane_s16
- arm_neon/int32x4_t
- arm_neon/vqadd_s8
- arm_neon/vld2q_f16
- arm_neon/vld2q_lane_p16
- arm_neon/vadd_u32
- arm_neon/vcntq_u8
- arm_neon/vst1_f32
- arm_neon/vmaxq_u32
- arm_neon/vsub_u64
- arm_neon/vsubl_s32
- arm_neon/poly16x4_t
- arm_neon/vgetq_lane_u16
- arm_neon/vdup_lane_s32
- arm_neon/vrhadd_s32
- arm_neon/veorq_u8
- arm_neon/vclzq_s8
- arm_neon/vsliq_n_s64
- arm_neon/vpadalq_s16
- arm_neon/vmla_n_f32
- arm_neon/vcgt_u16
- armintr/_arm_usada8
- arm_neon/vabd_u32
- arm_neon/vgetq_lane_s8
- arm_neon/vqshlq_n_u64
- arm_neon/vabaq_u32
- armintr/_arm_uhsax
- arm_neon/vmulq_f32
- arm_neon/vld3_dup_s16
- arm_neon/vst3_f16
- arm_neon/vrshrq_n_s64
- armintr/__rdpmccntr64
- arm_neon/vclsq_s32
- arm_neon/vmax_u16
- arm_neon/vmvnq_p8
- arm_neon/veor_u16
- arm_neon/vqshrn_n_u32
- arm_neon/vextq_u64
- arm_neon/vld1q_f32
- arm_neon/vget_low_u32
- arm_neon/vhaddq_s32
- arm_neon/vminq_u16
- arm_neon/vqrdmulhq_lane_s32
- arm_neon/vmla_s16
- arm_neon/vadd_s16
- arm_neon/vbsl_u16
- arm_neon/vhsub_s8
- arm_neon/vld4q_lane_p16
- arm_neon/vld1_s16
- arm_neon/vst2q_lane_p16
- arm_neon/vld2_dup_s8
- arm_neon/vst3q_s16
- arm_neon/vcgeq_u32
- arm_neon/vabdq_s16
- arm_neon/vrhadd_u16
- arm_neon/vqshlq_n_u32
- arm_neon/vst4q_lane_u32
- arm_neon/vrsraq_n_u64
- arm_neon/vmlsq_n_s32
- arm_neon/vld4_u8
- arm_neon/vld2_f16
- arm_neon/vqshlq_u8
- arm_neon/vorrq_u64
- arm_neon/vmin_u16
- arm_neon/vext_u8
- arm_neon/vpaddl_s32
- arm_neon/vshlq_u64
- arm_neon/vst2q_lane_f16
- armintr/_arm_sbfx
- arm_neon/vld3_dup_f16
- armintr/_arm_uhasx
- arm_neon/vst2_lane_u8
- armintr/_arm_smultb
- arm_neon/vdup_n_p16
- arm_neon/vtrnq_u32
- arm_neon/vrshlq_u8
- arm_neon/vld4_lane_p16
- arm_neon/vsraq_n_s32
- arm_neon/vclt_s16
- arm_neon/vzip_u8
- arm_neon/vld3_lane_s16
- arm_neon/vceqq_s32
- arm_neon/vld3_dup_f32
- arm_neon/vld4q_lane_s32
- arm_neon/poly8x16x4_t
- arm_neon/uint64x1x2_t
- arm_neon/vqdmlal_n_s16
- arm_neon/vld2_dup_f16
- arm_neon/vshrq_n_s32
- arm_neon/vcleq_s8
- arm_neon/vld3_s32
- arm_neon/vqrshlq_s64
- arm_neon/vbsl_f32
- arm_neon/vext_s64
- arm_neon/vabaq_s32
- arm_neon/vmulq_s16
- arm_neon/vld3_lane_u16
- arm_neon/vld3q_lane_u16
- armintr/_arm_smlaltt
- arm_neon/poly8x8x2_t
- arm_neon/vst3q_u32
- armintr/_arm_smlsdx
- arm_neon/vqrshl_s64
- arm_neon/vextq_p8
- armintr/_arm_uhsub16
- arm_neon/vld3q_p8
- armintr/_arm_smlawt
- armintr/_arm_smlawb
- arm_neon/vdupq_lane_s8
- arm_neon/vaddl_s16
- arm_neon/vcombine_p16
- arm_neon/vzipq_u32
- arm_neon/poly16x8_t
- arm_neon/vshlq_n_s32
- arm_neon/vrshl_s8
- arm_neon/vst2_u64
- arm_neon/vrev64q_s8
- arm_neon/vst2q_lane_s32
- arm_neon/vld2_dup_s16
- arm_neon/vclt_u16
- arm_neon/vuzp_p8
- arm_neon/vshrq_n_s16
- arm_neon/vst3_u64
- arm_neon/vpmin_u16
- arm_neon/vld3q_lane_s32
- arm_neon/vmlal_s16
- arm_neon/poly16x4x4_t
- arm_neon/vorr_u16
- arm_neon/vsliq_n_s16
- arm_neon/vaddl_u8
- arm_neon/vld4_dup_s32
- arm_neon/vld2_f32
- arm_neon/vclt_u32
- arm_neon/vmull_lane_u16
- arm_neon/vsubw_u32
- arm_neon/vld2_dup_s32
- arm_neon/vuzp_s32
- arm_neon/vcge_s32
- arm_neon/vdup_lane_p16
- arm_neon/vpmin_s8
- arm_neon/vpaddlq_u32
- arm_neon/vmlaq_n_s32
- arm_neon/vshrn_n_u64
- arm_neon/vrshr_n_u16
- arm_neon/vld1_s64
- arm_neon/vbsl_u64
- armintr/_arm_smlad
- arm_neon/vqsub_s16
- arm_neon/vld4_p8
- arm_neon/vqdmulh_lane_s32
- arm_neon/vld3_dup_s64
- arm_neon/vornq_s32
- arm_neon/vpadd_u8
- arm_neon/vld3_lane_p16
- arm_neon/uint64x1x4_t
- arm_neon/vld3_u16
- armintr/_arm_shsax
- arm_neon/vabdq_u16
- arm_neon/vcgtq_f32
- arm_neon/vsubq_s8
- arm_neon/vget_low_f16
- arm_neon/vld4_dup_u64
- arm_neon/vst3_lane_s8
- armintr/_arm_ssat16
- arm_neon/vmlaq_f32
- arm_neon/vsri_n_s32
- arm_neon/vmax_u8
- arm_neon/vqadd_u8
- armintr/_arm_uqsub8
- armintr/_arm_clz
- arm_neon/vcgtq_s32
- arm_neon/vraddhn_s32
- arm_neon/vzip_s8
- arm_neon/veorq_s16
- arm_neon/vsetq_lane_s32
- arm_neon/vmul_n_u16
- armintr/_ReadBankedReg
- arm_neon/vld1q_u8
- arm_neon/vld4_p16
- arm_neon/int64x2x2_t
- arm_neon/vmaxq_s8
- arm_neon/vpmax_s16
- arm_neon/vshlq_u16
- arm_neon/vtrnq_p16
- arm_neon/vabal_u16
- arm_neon/vld2_lane_u16
- arm_neon/vrev32_u8
- arm_neon/vrshl_s32
- arm_neon/vget_low_f32
- arm_neon/vld2_s8
- arm_neon/vclzq_s16
- arm_neon/vqdmulhq_n_s16
- arm_neon/vset_lane_u64
- arm_neon/vld2_dup_p16
- arm_neon/vpaddlq_s32
- arm_neon/vld2q_p8
- arm_neon/vst3_lane_u8
- arm_neon/vld4_dup_f32
- arm_neon/vld2_s64
- arm_neon/vmls_u8
- arm_neon/vtbx4_u8
- arm_neon/vsetq_lane_f32
- arm_neon/vcvt_s32_f32
- arm_neon/vst3q_s32
- arm_neon/vmlsq_s8
- arm_neon/vmlaq_n_u16
- armintr/__iso_volatile_load64
- arm_neon/vcgt_u8
- arm_neon/vld2_dup_p8
- arm_neon/vmov_n_u8
- armintr/_arm_sasx
- arm_neon/vmovq_n_p16
- arm_neon/vmlaq_u32
- arm_neon/vst3_f32
- arm_neon/int32x2x4_t
- arm_neon/vld1q_lane_u64
- arm_neon/vclz_u16
- arm_neon/uint8x8_t
- arm_neon/vsub_u32
- arm_neon/vorn_u8
- armintr/__wfe
- arm_neon/vget_high_s16
- arm_neon/vzip_p8
- arm_neon/vmlal_lane_s16
- arm_neon/vmulq_u8
- armintr/_isunordered
- arm_neon/vld1_dup_f32
- arm_neon/vld4_lane_s16
- arm_neon/vdupq_n_s16
- arm_neon/vst3q_p16
- arm_neon/vst1_lane_f32
- arm_neon/float32x4x3_t
- arm_neon/vand_s8
- arm_neon/float32x2x4_t
- arm_neon/vld3_p8
- arm_neon/vmlaq_lane_u16
- armintr/_arm_uqsub16
- arm_neon/vget_high_s32
- arm_neon/vshl_n_s32
- arm_neon/vornq_s8
- arm_neon/vmlsl_n_u32
- arm_neon/vqshlq_n_s8
- arm_neon/int32x2x2_t
- arm_neon/int16x4x2_t
- arm_neon/vceqq_u8
- arm_neon/vcreate_f16
- arm_neon/vorn_s16
- arm_neon/vqmovn_s32
- arm_neon/vextq_u8
- arm_neon/vld4_s32
- armintr/_WriteStatusReg
- arm_neon/uint8x16_t
- arm_neon/vshrn_n_s64
- arm_neon/vmul_n_u32
- arm_neon/vabdl_u8
- arm_neon/vtbx3_s8
- arm_neon/vaddhn_s16
- arm_neon/vld3q_s8
- arm_neon/vmlsl_n_u16
- arm_neon/vrev64q_s32
- arm_neon/int16x8_t
- arm_neon/vext_s32
- arm_neon/vdupq_n_f32
- arm_neon/vld1q_lane_s32
- arm_neon/vqrshlq_u32
- arm_neon/vtbl2_u8
- arm_neon/vgetq_lane_u8
- arm_neon/veorq_u64
- arm_neon/vcntq_s8
- arm_neon/vbslq_p16
- arm_neon/vqnegq_s32
- arm_neon/vaddw_s32
- arm_neon/vmov_n_p8
- arm_neon/vmull_p8
- arm_neon/vld1_lane_u32
- arm_neon/vcombine_s16
- arm_neon/vqshrn_n_s64
- arm_neon/vceqq_s16
- arm_neon/vld4q_p16
- armintr/_ReadStatusReg
- armintr/_arm_qdadd
- arm_neon/uint32x4x2_t
- arm_neon/vcleq_u8
- armintr/_arm_sxtah
- arm_neon/vrhaddq_s32
- arm_neon/vset_lane_s64
- arm_neon/vld4_s64
- armintr/_DAddSatInt
- arm_neon/vorr_s8
- arm_neon/vst2_u32
- arm_neon/vshll_n_u16
- arm_neon/vld2_dup_u32
- arm_neon/vst3q_lane_s32
- arm_neon/vst3q_p8
- armintr/_MoveFromCoprocessor
- arm_neon/uint32x4_t
- arm_neon/vuzpq_s8
- arm_neon/vrecps_f32
- arm_neon/vst1_lane_s8
- arm_neon/vtbx1_s8
- arm_neon/uint16x8x3_t
- arm_neon/vpaddl_s16
- arm_neon/vsubq_s64
- arm_neon/vrsraq_n_u8
- arm_neon/vqadd_s64
- arm_neon/vst4_lane_s16
- arm_neon/vqadd_u16
- arm_neon/vset_lane_u32
- arm_neon/vand_u32
- arm_neon/vrsqrtsq_f32
- arm_neon/vqaddq_u32
- arm_neon/vsra_n_s64
- armintr/_arm_umlal
- arm_neon/vcvt_f32_f16
- arm_neon/vget_lane_u32
- arm_neon/vbsl_s8
- arm_neon/vrshlq_u32
- arm_neon/vqdmull_lane_s16
- arm_neon/vabsq_s32
- arm_neon/vld3_s8
- arm_neon/vst3q_lane_s16
- arm_neon/vld2q_lane_s16
- arm_neon/vst1_lane_s64
- arm_neon/vmov_n_u16
- arm_neon/vst4_lane_u8
- arm_neon/vshll_n_u32
- arm_neon/vqabs_s8
- arm_neon/vmvnq_u8
- arm_neon/vpadalq_u16
- arm_neon/vbsl_p16
- arm_neon/vqrshrn_n_u16
- arm_neon/vld3q_u32
- arm_neon/vcgeq_f32
- armintr/__iso_volatile_load32
- arm_neon/vrecpe_u32
- arm_neon/vld2_dup_u64
- arm_neon/vld3q_f32
- armintr/_arm_shsub8
- arm_neon/vdup_lane_s64
- arm_neon/vqrshl_s8
- arm_neon/vsliq_n_u16
- arm_neon/vld1q_u16
- arm_neon/vorr_u32
- arm_neon/vqrshl_s32
- armintr/__dmb
- arm_neon/veorq_s8
- arm_neon/vld1_u16
- arm_neon/vmov_n_u32
- arm_neon/vhsub_s16
- arm_neon/vst4q_lane_u16
- arm_neon/vbsl_u8
- armintr/_arm_uxtab
- arm_neon/vld2q_lane_f32
- arm_neon/vst2_p8
- armintr/_arm_smmla
- arm_neon/vaddw_u16
- arm_neon/vmlal_s8
- arm_neon/vtst_u32
- arm_neon/vtbl4_u8
- arm_neon/vcvt_n_f32_s32
- arm_neon/vcageq_f32
- arm_neon/vget_low_s16
- arm_neon/vdupq_n_u8
- arm_neon/vorn_s8
- arm_neon/uint8x16x3_t
- arm_neon/vabdq_u32
- arm_neon/vrev64_p8
- arm_neon/vqsubq_s8
- armintr/_arm_smlabb
- arm_neon/vbicq_s64
- arm_neon/vmaxq_u16
- arm_neon/vdup_n_u8
- arm_neon/veor_s8
- arm_neon/int16x8x2_t
- arm_neon/vcvtq_s32_f32
- arm_neon/vtrn_u16
- arm_neon/vbslq_s32
- arm_neon/vld1q_dup_u32
- arm_neon/vmul_n_f32
- arm_neon/vqrshl_u32
- arm_neon/vqsubq_s16
- arm_neon/vst2_lane_f16
- armintr/_arm_smulwt
- arm_neon/vrshrn_n_u32
- arm_neon/vget_high_p16
- arm_neon/vqadd_u64
- arm_neon/vsli_n_s32
- arm_neon/vhadd_u32
- arm_neon/vmlsl_lane_u16
- arm_neon/vclzq_u32
- arm_neon/vqshrun_n_s64
- arm_neon/vrev64q_u32
- arm_neon/vqshrun_n_s16
- arm_neon/vrev32q_s8
- armintr/_arm_shasx
- arm_neon/vaddl_s8
- armintr/_arm_smull
- arm_neon/vabaq_u8
- armintr/_arm_revsh
- arm_neon/vsubq_f32
- arm_neon/poly16x4x2_t
- arm_neon/poly8x8x3_t
- arm_neon/vsubhn_s64
- arm_neon/vcle_u16
- arm_neon/poly8x16x3_t
- arm_neon/vqdmlsl_n_s16
- arm_neon/vqshl_u64
- arm_neon/vcge_u16
- armintr/_arm_uasx
- arm_neon/vmovl_s32
- arm_neon/vst1q_lane_u16
- arm_neon/vbic_u32
- arm_neon/vld2_s16
- armintr/_arm_qasx
- arm_neon/vorrq_u8
- arm_neon/vst2_s32
- armintr/_WriteBankedReg
- arm_neon/veorq_s64
- arm_neon/vld4_lane_f32
- arm_neon/vcreate_u8
- arm_neon/vset_lane_u8
- arm_neon/vandq_u16
- arm_neon/vrsubhn_s64
- arm_neon/vst1q_lane_p16
- arm_neon/uint8x8x2_t
- arm_neon/vmlsl_s8
- arm_neon/vmax_s32
- arm_neon/uint32x4x3_t
- arm_neon/vld4_dup_u16
- arm_neon/vabs_s32
- arm_neon/vld3_dup_u32
- arm_neon/vrshl_u16
- arm_neon/vcle_u8
- arm_neon/vqshl_n_u16
- arm_neon/vbic_s8
- arm_neon/float32x4x2_t
- arm_neon/vmls_f32
- arm_neon/vshll_n_u8
- arm_neon/vminq_s8
- arm_neon/vmlsq_lane_f32
- arm_neon/vst1q_f16
- arm_neon/vst1_lane_u64
- arm_neon/vrhadd_u8
- arm_neon/vclt_s32
- arm_neon/vst2_p16
- arm_neon/vrshrq_n_u16
- arm_neon/vneg_s32
- arm_neon/vmovl_s16
- arm_neon/vqshlq_s8
- arm_neon/vld1_s8
- arm_neon/vqdmulh_s32
- arm_neon/vcls_s8
- armintr/__trap
- arm_neon/vuzp_u32
- armintr/_CopyInt64FromDouble
- arm_neon/int8x16x2_t
- arm_neon/vmovn_s32
- arm_neon/vget_high_s8
- arm_neon/veor_s64
- armintr/_arm_uadd8
- arm_neon/vrev16_u8
- arm_neon/vbicq_u64
- arm_neon/vst4_lane_f16
- arm_neon/vst3_s32
- arm_neon/poly8x8_t
- arm_neon/vtstq_u16
- arm_neon/vld1_lane_s8
- arm_neon/float32x4x4_t
- arm_neon/vst2_s16
- arm_neon/vqrdmulhq_s32
- arm_neon/vqdmulhq_s16
- arm_neon/vrshrq_n_s8
- arm_neon/vcle_s32
- arm_neon/vtbl3_p8
- arm_neon/vbslq_u8
- arm_neon/vst4_u64
- armintr/_arm_umaal
- arm_neon/vshll_n_s8
- arm_neon/vcvt_u32_f32
- arm_neon/vld4q_p8
- arm_neon/vsetq_lane_u16
- arm_neon/vabd_u8
- arm_neon/vclz_u8
- arm_neon/vsubq_u32
- arm_neon/vld1q_lane_p16
- arm_neon/vcgtq_s16
- arm_neon/vmla_lane_s32
- arm_neon/vshlq_n_s64
- arm_neon/vbsl_u32
- arm_neon/vqshlq_s16
- armintr/_arm_qadd8
- arm_neon/vrshr_n_s32
- armintr/_CountOneBits64
- arm_neon/vceq_u32
- arm_neon/vbsl_p8
- arm_neon/uint16x8x2_t
- arm_neon/vsli_n_s16
- arm_neon/vmla_n_s32
- arm_neon/vld4_dup_u32
- arm_neon/vshrq_n_s8
- arm_neon/vqaddq_s8
- arm_neon/vshl_n_u64
- arm_neon/vtbl2_p8
- arm_neon/vcleq_u32
- arm_neon/vqsub_u32
- arm_neon/vmovl_u8
- arm_neon/vmlal_u8
- arm_neon/vmul_s8
- armintr/_MoveFromCoprocessor64
- arm_neon/vrsraq_n_s16
- arm_neon/vdupq_n_u32
- arm_neon/vmov_n_s16
- arm_neon/vst4_lane_p8
- arm_neon/vld1_s32
- arm_neon/vst4_p8
- arm_neon/vsriq_n_u32
- arm_neon/vqdmull_n_s16
- arm_neon/vshlq_u32
- arm_neon/vld3_u8
- armintr/_arm_usub16
- arm_neon/vmlsq_lane_s16
- arm_neon/vmovq_n_s8
- arm_neon/int32x4x2_t
- arm_neon/vld4q_u8
- arm_neon/poly16x8x2_t
- arm_neon/vld1q_u64
- arm_neon/vld3q_lane_s16
- arm_neon/int64x1x2_t
- arm_neon/vshlq_n_s8
- arm_neon/vrshl_s64
- arm_neon/vqshl_n_u8
- armintr/_arm_qadd
- armintr/_DSubSatInt
- armintr/_arm_usat16
- arm_neon/vmull_s8
- arm_neon/vsub_s8
- arm_neon/vmovq_n_u16
- arm_neon/vst4_u16
- arm_neon/vmlsl_lane_u32
- arm_neon/vsliq_n_p16
- arm_neon/vmovn_u32
- arm_neon/vbic_u16
- arm_neon/vtbx2_p8
- arm_neon/vrsubhn_s32
- armintr/_SubSatInt
- arm_neon/vst3_u8
- arm_neon/vdupq_n_s32
- arm_neon/vcntq_p8
- arm_neon/vst4_f32
- arm_neon/vbic_s64
- arm_neon/vld3_s64
- arm_neon/vrsra_n_s64
- arm_neon/vqabsq_s16
- arm_neon/vsriq_n_p8
- arm_neon/vst2_lane_p16
- arm_neon/vabsq_s16
- arm_neon/vcombine_u8
- arm_neon/vld2q_p16
- armintr/_CountOneBits
- armintr/__prefetch
- arm_neon/vld3_dup_u64
- arm_neon/vld2q_s16
- arm_neon/vget_low_p16
- arm_neon/vuzpq_u8
- arm_neon/vrev32q_s16
- armintr/_AddSatInt
- arm_neon/uint16x4x2_t
- arm_neon/vmov_n_s32
- arm_neon/vaddl_u16
- arm_neon/vqaddq_s64
- arm_neon/vmlaq_u16
- arm_neon/vsli_n_s8
- armintr/_arm_sxth
- arm_neon/vorr_s32
- arm_neon/vsra_n_u64
- arm_neon/vst2_f16
- arm_neon/vcombine_u16
- arm_neon/vabs_s16
- arm_neon/vsubhn_s32
- arm_neon/vst1q_lane_u32
- arm_neon/vst3_p8
- arm_neon/vqshrun_n_s32
- arm_neon/vcreate_s64
- arm_neon/vld4q_lane_s16
- arm_neon/vzipq_u16
- arm_neon/vmin_s32
- armintr/_CopyInt32FromFloat
- arm_neon/vcgtq_u32
- arm_neon/vabdl_s32
- arm_neon/vqshlq_n_u16
- arm_neon/int8x16x4_t
- arm_neon/vqrdmulh_n_s32
- arm_neon/vqaddq_u64
- arm_neon/vhaddq_s8
- arm_neon/vshll_n_s16
- arm_neon/vuzp_u8
- arm_neon/vaddl_u32
- arm_neon/vld4q_s16
- arm_neon/vqmovun_s16
- arm_neon/vld1q_lane_s8
- arm_neon/vld2_lane_u32
- arm_neon/vrshr_n_s8
- arm_neon/vmlaq_s16
- armintr/_CopyFloatFromInt32
- arm_neon/vmul_f32
- arm_neon/vmlaq_n_f32
- arm_neon/vst4_s16
- arm_neon/vld1_dup_s32
- arm_neon/vmul_u16
- arm_neon/vhaddq_s16
- arm_neon/vst1q_lane_f32
- arm_neon/vrhaddq_u16
- arm_neon/vbicq_u32
- arm_neon/vrev32_s8
- arm_neon/vmlaq_s8
- arm_neon/vmin_s16
- arm_neon/vst3_lane_p16
- arm_neon/vst2q_lane_f32
- arm_neon/vld4q_lane_f32
- arm_neon/vget_low_u16
- arm_neon/vqsub_s32
- arm_neon/vtbl1_s8
- arm_neon/vmovn_s64
- arm_neon/vpmax_s8
- arm_neon/int8x16_t
- arm_neon/vpmin_u8
- arm_neon/vdup_lane_p8
- arm_neon/vsetq_lane_u64
- arm_neon/vuzpq_u16
- arm_neon/vcgeq_u16
- arm_neon/uint8x16x2_t
- armintr/_arm_rev16
- armintr/_arm_sxtb
- arm_neon/vsliq_n_u64
- arm_neon/vmovq_n_u8
- arm_neon/vshlq_n_u32
- arm_neon/vcombine_s64
- armintr/_arm_qsax
- arm_neon/vmin_f32
- armintr/_arm_sadd16
- arm_neon/vmlsq_n_s16
- arm_neon/vorr_u64
- arm_neon/vqrshrun_n_s64
- arm_neon/vld2q_lane_s32
- arm_neon/vgetq_lane_p16
- arm_neon/vrev32_s16
- arm_neon/vqshl_u16
- arm_neon/vtrn_s8
- arm_neon/vst1q_lane_s64
- arm_neon/vtbl4_p8
- arm_neon/vst1_p16
- arm_neon/vmvn_u8
- arm_neon/vld2_lane_u8
- arm_neon/vld2q_u16
- arm_neon/vmovl_s8
- arm_neon/vbslq_u64
- arm_neon/vmls_s8
- arm_neon/vld3q_p16
- arm_neon/vtbl3_u8
- arm_neon/vabs_f32
- arm_neon/vsraq_n_s8
- arm_neon/vqadd_s32
- arm_neon/vmulq_n_s16
- arm_neon/vst3q_s8
- arm_neon/vaddhn_s64
- arm_neon/vmul_n_s16
- arm_neon/vtbl1_p8
- arm_neon/uint64x2x3_t
- arm_neon/vmlsq_s32
- arm_neon/vld2q_lane_u32
- arm_neon/vaddq_u8
- arm_neon/vcombine_f16
- arm_neon/vandq_s16
- arm_neon/vst4q_lane_p16
- arm_neon/vsri_n_u8
- arm_neon/vst3_lane_p8
- arm_neon/vst3_lane_s16
- arm_neon/vdup_n_s16
- arm_neon/vbicq_s8
- arm_neon/vdup_lane_u8
- arm_neon/vst4q_lane_s32
- arm_neon/vqrshl_u16
- arm_neon/vrsra_n_u32
- arm_neon/vdupq_lane_p8
- arm_neon/vld3_lane_u8
- arm_neon/vqrdmulh_n_s16
- arm_neon/vpmin_s32
- armintr/__cps
- arm_neon/vshl_u32
- armintr/_arm_uadd16
- arm_neon/vld3_s16
- arm_neon/vcvt_f32_s32
- arm_neon/vshlq_n_u64
- arm_neon/vrev64q_u8
- arm_neon/vextq_u16
- arm_neon/vsubl_s16
- arm_neon/vget_lane_p8
- arm_neon/vabal_s16
- arm_neon/vrecpeq_u32
- arm_neon/vminq_u8
- arm_neon/veor_s16
- arm_neon/vmull_n_u16
- arm_neon/vshl_n_u8
- arm_neon/vrev32q_u8
- arm_neon/vandq_s8
- arm_neon/vrshlq_s16
- arm_neon/vst4q_p16
- arm_neon/vandq_s32
- armintr/_MoveToCoprocessor2
- arm_neon/vqdmlsl_lane_s32
- arm_neon/vld1q_s64
- arm_neon/vmull_n_s16
- arm_neon/vneg_s16
- arm_neon/vqshluq_n_s64
- arm_neon/vst2_lane_s32
- arm_neon/vmvnq_u16
- arm_neon/vshll_n_s32
- arm_neon/vld3_dup_s8
- arm_neon/vtstq_s32
- arm_neon/vmlsl_u32
- arm_neon/vqdmulhq_lane_s16
- arm_neon/vaddl_s32
- armintr/_CountLeadingZeros
- arm_neon/vqrshrn_n_s16
- arm_neon/vmla_lane_u32
- arm_neon/vst1_u8
- arm_neon/vshl_u64
- arm_neon/vshr_n_u8
- arm_neon/vmull_lane_s32
- arm_neon/vmlal_lane_u32
- arm_neon/vsubl_s8
- arm_neon/float32x2x2_t
- armintr/_arm_bfc
- arm_neon/vaddq_s16
- arm_neon/vmlal_lane_s32
- arm_neon/vpadd_u16
- arm_neon/vst2q_lane_u16
- arm_neon/vld4_s8
- arm_neon/vst1q_s8
- arm_neon/vshrq_n_u64
- arm_neon/vsli_n_u16
- arm_neon/vqrdmulh_lane_s32
- arm_neon/vst4_lane_u16
- arm_neon/vabdq_f32
- arm_neon/vld2_lane_f16
- arm_neon/vqsub_u64
- arm_neon/vsub_f32
- arm_neon/vld1q_s16
- arm_neon/vmaxq_s16
- arm_neon/vcombine_u32
- arm_neon/vrsraq_n_u32
- armintr/_arm_smusdx
- arm_neon/vrev16_s8
- arm_neon/vqdmulh_n_s32
- arm_neon/vmul_s32
- arm_neon/vabdq_s32
- arm_neon/veor_u64
- arm_neon/vmlsl_n_s32
- arm_neon/vsub_s16
- arm_neon/vadd_u16
- arm_neon/vsriq_n_u16
- arm_neon/vmla_u32
- arm_neon/vuzpq_s32
- arm_neon/vst4q_s8
- arm_neon/vaddhn_u32
- arm_neon/vmlaq_lane_f32
- arm_neon/vld3_lane_s8
- arm_neon/vsliq_n_u32
- arm_neon/vqrshlq_s8
- arm_neon/vqdmlal_n_s32
- arm_neon/uint8x16x4_t
- arm_neon/vcgtq_u16
- arm_neon/vandq_u32
- arm_neon/vld4q_lane_u32
- arm_neon/vzip_p16
- arm_neon/vget_low_p8
- armintr/_arm_shadd8
- arm_neon/vmovn_s16
- arm_neon/vcge_u8
- arm_neon/vld2q_f32
- arm_neon/vaba_u32
- armintr/__iso_volatile_store8
- arm_neon/vst2q_p16
- arm_neon/vmul_s16
- arm_neon/vand_s16
- arm_neon/vtbx4_p8
- arm_neon/vceq_u8
- arm_neon/vrhaddq_s16
- arm_neon/vgetq_lane_f32
- arm_neon/vqshl_s8
- arm_neon/vbslq_f32
- arm_neon/vrsqrts_f32
- arm_neon/vld2q_s8
- arm_neon/vtbl1_u8
- arm_neon/vtst_u8
- arm_neon/vrev64q_f32
- arm_neon/vcle_s8
- arm_neon/vsetq_lane_p16
- arm_neon/vcreate_p16
- arm_neon/vabal_s32
- armintr/_arm_smlald
- arm_neon/vmla_f32
- arm_neon/vtbx2_s8
- arm_neon/int64x1x3_t
- arm_neon/vclz_s8
- arm_neon/vorr_s16
- arm_neon/vornq_s64
- arm_neon/vst1q_u64
- arm_neon/vdupq_n_s8
- armintr/_arm_sadd8
- arm_neon/vextq_s32
- armintr/_arm_smuadx
- armintr/_arm_qsub
- arm_neon/vadd_f32
- arm_neon/vrshrq_n_s16
- arm_neon/vqsub_s8
- arm_neon/vld3_f32
- arm_neon/vhadd_s8
- arm_neon/vmull_n_u32
- arm_neon/vdup_n_u64
- arm_neon/vsubw_s32
- armintr/_arm_sxtab
- armintr/_arm_uxtb16
- arm_neon/vmvn_s16
- arm_neon/vst1_lane_s16
- arm_neon/vqrdmulhq_n_s32
- arm_neon/vsriq_n_s32
- arm_neon/poly8x16x2_t
- arm_neon/vadd_u8
- arm_neon/vuzpq_p8
- arm_neon/vst2q_p8
- armintr/__wfi
- arm_neon/vget_high_u16
- arm_neon/vqrshl_u64
- arm_neon/vld1_dup_s64
- arm_neon/vqrshrn_n_s32
- arm_neon/vrshr_n_s64
- arm_neon/vst3_s8
- arm_neon/poly16x4x3_t
- arm_neon/vqrdmulh_lane_s16
- arm_neon/vmvnq_u32
- arm_neon/vqsubq_u32
- arm_neon/vmovq_n_p8
- arm_neon/vtrn_s16
- arm_neon/vld2q_u32
- arm_neon/vqsubq_u16
- arm_neon/vrsqrteq_u32
- arm_neon/vadd_u64
- armintr/_arm_usat
- arm_neon/vcvtq_n_u32_f32
- arm_neon/vaddq_s8
- arm_neon/vrsraq_n_u16
- arm_neon/vqabs_s16
- arm_neon/vsra_n_s8
- arm_neon/vsra_n_s16
- arm_neon/vqshlq_n_u8
- arm_neon/vpadal_s8
- arm_neon/vmlal_n_u16
- armintr/_CopyDoubleFromInt64
- arm_neon/vaddw_u8
- arm_neon/vmulq_n_s32
- arm_neon/vqaddq_s32
- arm_neon/vmla_lane_f32
- arm_neon/vmlaq_lane_s32
- arm_neon/vld1q_dup_u64
- arm_neon/uint16x8_t
- arm_neon/vld2_s32
- arm_neon/vcltq_f32
- arm_neon/vst4q_f32
- arm_neon/vsri_n_u16
- arm_neon/vshlq_s32
- arm_neon/vgetq_lane_u32
- arm_neon/vld1q_dup_f16
- arm_neon/vrev64q_s16
- arm_neon/vrshrq_n_u32
- arm_neon/vld2q_s32
- arm_neon/vcgtq_s8
- arm_neon/vsubhn_u64
- arm_neon/vmls_n_s32
- armintr/_arm_smmlar
- arm_neon/vld3_dup_u8
- arm_neon/vld3q_lane_p16
- arm_neon/vld2_dup_s64
- arm_neon/vqabs_s32
- arm_neon/vqaddq_u8
- arm_neon/vminq_u32
- arm_neon/vpaddl_u16
- arm_neon/vaba_s16
- arm_neon/vmul_u32
- arm_neon/vst1_lane_u16
- arm_neon/vcreate_f32
- arm_neon/vcvt_f16_f32
- arm_neon/vset_lane_s32
- arm_neon/vshl_s8
- arm_neon/vcgt_s16
- arm_neon/vtrn_f32
- arm_neon/vget_high_s64
- arm_neon/vld3_dup_p8
- arm_neon/vcreate_u64
- arm_neon/vext_u64
- arm_neon/vld1q_dup_s16
- arm_neon/vget_lane_s16
- arm_neon/vqdmlal_s16
- arm_neon/vld2_p16
- arm_neon/vld4_u16
- armintr/_arm_smlalbb
- arm_neon/vrev64_u8
- arm_neon/vbslq_s64
- arm_neon/vsubw_u16
- arm_neon/vrsubhn_u32
- arm_neon/vabdq_u8
- arm_neon/vmls_n_u32
- arm_neon/vshr_n_s32
- arm_neon/vmulq_n_u32
- arm_neon/vst3_p16
- arm_neon/vrev32_u16
- arm_neon/int8x8x3_t
- arm_neon/vst2q_lane_u32
- arm_neon/vextq_p16
- arm_neon/vtrnq_f32
- armintr/_arm_smultt
- arm_neon/vqneg_s8
- arm_neon/vmlsq_lane_s32
- arm_neon/vmov_n_p16
- arm_neon/vraddhn_u64
- arm_neon/vrhadd_u32
- arm_neon/vrev64_u32
- arm_neon/vrshrn_n_s32
- arm_neon/vld4q_f32
- arm_neon/vst2_s8
- arm_neon/vrsqrteq_f32
- arm_neon/uint16x4_t
- arm_neon/vget_low_s8
- arm_neon/vst2_lane_u32
- arm_neon/vhsub_s32
- arm_neon/vqdmull_lane_s32
- armintr/_arm_smulwb
- arm_neon/vmlsl_u8
- arm_neon/vdup_lane_s16
- arm_neon/vtbx4_s8
- arm_neon/vld4q_lane_u16
- arm_neon/vget_high_u8
- arm_neon/vclzq_s32
- arm_neon/vld1q_dup_f32
- arm_neon/vtrn_u8
- arm_neon/vqabsq_s8
- arm_neon/vdup_lane_f32
- arm_neon/vqrdmulh_s16
- arm_neon/vst4_u32
- arm_neon/vdup_lane_u32
- arm_neon/vst4_u8
- arm_neon/vmovq_n_s32
- arm_neon/vld2_lane_s8
- arm_neon/vld3_u32
- arm_neon/vsubl_u16
- arm_neon/vqshlu_n_s8
- arm_neon/float32x4_t
- arm_neon/vqshl_n_s32
- arm_neon/float32x2x3_t
- armintr/__hvc
- arm_neon/vst1q_lane_f16
- arm_neon/vmvnq_s16
- arm_neon/vst3q_lane_f32
- arm_neon/vld1q_dup_u8
- arm_neon/vmlsq_s16
- arm_neon/vget_lane_u8
- arm_neon/vld1_lane_s32
- arm_neon/vst4q_s16
- armintr/_arm_qsub8
- arm_neon/vorrq_s32
- arm_neon/vsriq_n_s8
- arm_neon/vqshrn_n_u64
- arm_neon/vdup_n_s32
- armintr/_arm_uhsub8
- arm_neon/vld3_lane_s32
- arm_neon/vbsl_s64
- arm_neon/vld1_dup_f16
- arm_neon/vsli_n_u64
- arm_neon/vraddhn_u32
- arm_neon/vsub_u16
- arm_neon/vcltq_u32
- arm_neon/vminq_f32
- arm_neon/vshl_n_s64
- arm_neon/vld4_u32
- arm_neon/vld1_u32
- arm_neon/vaddhn_u16
- arm_neon/vcvtq_n_f32_s32
- arm_neon/vorn_u64
- arm_neon/vsubhn_u16
- arm_neon/int64x1_t
- arm_neon/vst1q_lane_s8
- arm_neon/vld1q_dup_s32
- arm_neon/vrev32_p8
- arm_neon/vst3q_lane_p16
- arm_neon/vrecpeq_f32
- arm_neon/int8x8x4_t
- arm_neon/vshr_n_u32
- arm_neon/vdupq_lane_s64
- arm_neon/vpaddlq_s8
- arm_neon/vqshl_n_u32
- arm_neon/vmul_u8
- arm_neon/vtbx2_u8
- arm_neon/vshr_n_u64
- arm_neon/vqrshlq_s16
- arm_neon/vst3_lane_u16
- arm_neon/vqsub_u8
- arm_neon/vrsra_n_s16
- arm_neon/vaba_s32
- arm_neon/vsri_n_u64
- arm_neon/vst3q_lane_u32
- arm_neon/vmlsq_n_u32
- arm_neon/poly8x16_t
- arm_neon/vld2_u8
- armintr/_arm_smmulr
- arm_neon/vtst_s16
- armintr/_arm_smmls
- arm_neon/vqdmulh_s16
- arm_neon/vtrnq_u8
- arm_neon/vset_lane_p8
- arm_neon/vmlsl_u16
- arm_neon/vshrn_n_u16
- arm_neon/vld1_dup_p8
- arm_neon/vrev16q_s8
- arm_neon/vmov_n_s8
- arm_neon/vld1_u64
- arm_neon/vpmin_f32
- arm_neon/vmla_n_u16
- arm_neon/vst1_f16
- arm_neon/vqdmlsl_s16
- arm_neon/vmin_u32
- armintr/_arm_qsub16
- arm_neon/vcage_f32
- arm_neon/vornq_u32
- arm_neon/vpadd_s16
- arm_neon/vld1_u8
- arm_neon/vhsubq_s16
- arm_neon/vld1_dup_u32
- arm_neon/vld4_u64
- armintr/_MulHigh
- arm_neon/vmaxq_u8
- arm_neon/vget_lane_u16
- arm_neon/vld2q_u8
- arm_neon/vld1q_dup_p16
- arm_neon/vsraq_n_u8
- arm_neon/vqdmlsl_n_s32
- arm_neon/vst1_s16
- arm_neon/vst1q_s32
- arm_neon/vmaxq_f32
- arm_neon/vqdmulh_lane_s16
- armintr/__isb
- arm_neon/vuzpq_p16
- arm_neon/vmls_lane_s16
- arm_neon/vtbl4_s8
- arm_neon/vst1_lane_p8
- arm_neon/vsubw_s8
- arm_neon/vmin_u8
- arm_neon/vzip_u16
- arm_neon/vld4q_u16
- arm_neon/vshrn_n_s32
- arm_neon/vpadal_u16
- arm_neon/vorrq_s8
- arm_neon/vrshlq_u64
- arm_neon/vst3_lane_s32
- arm_neon/vqshluq_n_s32
- armintr/_arm_shsub16
- arm_neon/vst1_u32
- arm_neon/vrhadd_s16
- arm_neon/vzipq_s32
- arm_neon/vshrq_n_u16
- arm_neon/vcls_s32
- arm_neon/vceq_s8
- arm_neon/vld2q_lane_f16
- arm_neon/vst4q_u8
- arm_neon/vraddhn_u16
- arm_neon/vget_lane_u64
- armintr/_arm_smlsld
- arm_neon/vld3_u64
- arm_neon/vld1_lane_s16
- arm_neon/vabd_f32
- arm_neon/vdupq_n_u16
- armintr/__iso_volatile_store64
- arm_neon/vqsubq_u8
- arm_neon/poly16x8x3_t
- arm_neon/vcltq_s32
- arm_neon/vqnegq_s16
- arm_neon/vqsub_u16
- arm_neon/vaddq_s32
- arm_neon/vqshl_n_s64
- arm_neon/vabdl_s8
- arm_neon/vclsq_s16
- arm_neon/vpaddl_u8
- arm_neon/vmlsq_n_u16
- armintr/_arm_uqadd8
- arm_neon/vhsub_u32
- arm_neon/vset_lane_s16
- arm_neon/vsubl_u32
- arm_neon/vld3_lane_f32
- arm_neon/vcle_s16
- arm_neon/vmovl_u32
- arm_neon/vst3_lane_f16
- arm_neon/vcaltq_f32
- arm_neon/vsubq_s32
- arm_neon/vand_s64
- arm_neon/vst2_u8
- arm_neon/vcombine_p8
- arm_neon/vqdmlal_s32
- arm_neon/vsub_s32
- armintr/_arm_uxtab16
- arm_neon/vmlsq_n_f32
- armintr/_arm_qdsub
- arm_neon/vhaddq_u32
- arm_neon/vhsubq_u16
- arm_neon/vmlsq_lane_u16
- arm_neon/vst4_s64
- armintr/_CountLeadingOnes
- armintr/_arm_smlabt
- arm_neon/vcombine_s32
- arm_neon/vld4_lane_f16
- arm_neon/vadd_s64
- arm_neon/vorrq_u32
- armintr/__sev
- arm_neon/vdupq_lane_s32
- arm_neon/vrecpsq_f32
- arm_neon/vbicq_u16
- arm_neon/vld1_lane_p16
- arm_neon/vrshr_n_u32
- arm_neon/vcgeq_s32
- arm_neon/vld4_dup_s16
- arm_neon/vld1q_p8
- arm_neon/vrshlq_u16
- arm_neon/vmlaq_lane_u32
- arm_neon/vsub_s64
- arm_neon/vcreate_u16
- arm_neon/vget_lane_s32
- arm_neon/vuzp_f32
- arm_neon/vld2_lane_p8
- arm_neon/vuzp_u16
- arm_neon/vorrq_s16
- armintr/_arm_smlaltb
- arm_neon/vrshrn_n_s16
- arm_neon/vabd_s8
- arm_neon/vnegq_s8
- arm_neon/vst4q_u16
- arm_neon/vst1q_lane_s32
- arm_neon/vst1_lane_s32
- arm_neon/vmla_u16
- arm_neon/vmls_lane_s32
- arm_neon/vtst_s8
- arm_neon/vcgeq_s8
- arm_neon/poly8x8x4_t
- arm_neon/vqsub_s64
- armintr/_arm_uqasx
- arm_neon/vld1_lane_u64
- arm_neon/vminq_s16
- arm_neon/vmulq_u32
- arm_neon/vqrshlq_u8
- arm_neon/vdupq_n_p16
- arm_neon/vld4_dup_f16
- arm_neon/vcls_s16
- arm_neon/vmov_n_u64
- arm_neon/vmla_s32
- arm_neon/vrshl_s16
- arm_neon/vcalt_f32
- arm_neon/int64x2x3_t
- arm_neon/vsub_u8
- arm_neon/vzipq_u8
- arm_neon/vrshrn_n_u64
- arm_neon/vrshlq_s32
- arm_neon/vorr_s64
- arm_neon/vqrshl_s16
- arm_neon/vceqq_u16
- arm_neon/vmulq_n_u16
- arm_neon/vmlaq_u8
- arm_neon/vsri_n_s64
- arm_neon/vld3q_u8
- arm_neon/vld1_dup_s16
- arm_neon/vld1q_s32
- arm_neon/vsri_n_s16
- arm_neon/vshlq_u8
- arm_neon/vsli_n_s64
- arm_neon/vmull_lane_u32
- arm_neon/vshl_s64
- arm_neon/vcreate_s16
- arm_neon/uint8x8x4_t
- arm_neon/vqshrn_n_s32
- arm_neon/vqshlq_u32
- arm_neon/vmlal_n_u32
- arm_neon/vtrnq_s16
- arm_neon/vshr_n_s64
- arm_neon/vst2_u16
- arm_neon/vtrn_s32
- arm_neon/vsubhn_u32
- arm_neon/vbicq_s16
- arm_neon/vsetq_lane_s8
- arm_neon/vrsubhn_s16
- arm_neon/vhsub_u8
- arm_neon/vcleq_s32
- arm_neon/vld4_dup_s8
- arm_neon/vmull_u32
- arm_neon/vrshr_n_s16
- arm_neon/vst1q_lane_s16
- arm_neon/vmlsq_lane_u32
- arm_neon/vnegq_f32
- arm_neon/vmin_s8
- arm_neon/vrev16_p8
- arm_neon/vbic_u8
- arm_neon/vclzq_u16
- arm_neon/vcge_u32
- arm_neon/vget_high_u64
- arm_neon/vabsq_s8
- arm_neon/vhaddq_u16
- arm_neon/vsraq_n_s64
- arm_neon/vld2_u32
- arm_neon/vld2_lane_f32
- arm_neon/vqrshrn_n_u32
- arm_neon/vbslq_s8
- armintr/_CountLeadingZeros64
- arm_neon/vbicq_u8
- arm_neon/vdup_lane_s8
- arm_neon/vpadd_s32
- arm_neon/vld3q_lane_f16
- arm_neon/vaba_u8
- arm_neon/vqshlq_u16
- arm_neon/vst1q_u8
- arm_neon/vst4q_lane_f16
- arm_neon/vshl_n_u16
- armintr/_arm_smladx
- arm_neon/vmla_lane_s16
- arm_neon/vornq_u8
- arm_neon/vqneg_s32
- arm_neon/vadd_s8
- arm_neon/vcle_u32
- arm_neon/vclzq_u8
- arm_neon/vtbx1_u8
- armintr/_CountLeadingOnes64
- armintr/__dsb
- arm_neon/vaddq_u32
- arm_neon/vclsq_s8
- arm_neon/vdup_n_s64
- arm_neon/vmax_s16
- arm_neon/vst2q_u32
- arm_neon/vsetq_lane_s64
- arm_neon/vtst_p8
- arm_neon/vabs_s8
- arm_neon/vqshl_n_s16
- arm_neon/vqrshrn_n_u64
- arm_neon/vaddw_s8
- armintr/_arm_uhadd16
- arm_neon/vsriq_n_p16
- arm_neon/vld4_lane_u32
- arm_neon/vneg_f32
- armintr/_MoveToCoprocessor
- arm_neon/vmvnq_s8
- arm_neon/vld1q_lane_p8
- arm_neon/uint32x2x3_t
- arm_neon/vrshrn_n_u16
- arm_neon/vld3_f16
- arm_neon/vsriq_n_s16
- arm_neon/vshlq_n_s16
- arm_neon/vabal_u8
- arm_neon/vqshluq_n_s16
- arm_neon/vst2_lane_u16
- arm_neon/vbic_s16
- arm_neon/vqshl_n_u64
- arm_neon/vcagt_f32
- arm_neon/vpadalq_s8
- arm_neon/vclz_s32
- arm_neon/vld1_lane_s64
- arm_neon/vget_high_p8
- arm_neon/uint64x1_t
- arm_neon/vextq_s16
- arm_neon/vpadd_s8
- arm_neon/vrsubhn_u64
- arm_neon/vst3q_f16
- arm_neon/vdupq_lane_u16
- arm_neon/vrshrq_n_u64
- arm_neon/vmovq_n_f32
- arm_neon/vld1q_dup_u16
- arm_neon/vshr_n_u16
- arm_neon/uint32x2_t
- armintr/_arm_umull
- arm_neon/vtrnq_u16
- arm_neon/vsetq_lane_u32
- arm_neon/vneg_s8
- arm_neon/vsetq_lane_u8
- arm_neon/vst2q_lane_s16
- arm_neon/vqmovun_s32
- armintr/_arm_usad8
- armintr/_arm_pkhbt
- arm_neon/uint16x4x3_t
- arm_neon/vsra_n_s32
- arm_neon/vqmovun_s64
- arm_neon/vld1q_dup_s8
- arm_neon/vaddhn_s32
- arm_neon/vpmax_f32
- arm_neon/vpadd_u32
- arm_neon/vhsubq_u32
- arm_neon/vqrshrun_n_s32
- arm_neon/vadd_s32
- arm_neon/vclt_s8
- arm_neon/vorrq_s64
- arm_neon/vst4q_f16
- arm_neon/vst1_s32
- arm_neon/vceq_p8
- arm_neon/vsubw_s16
- arm_neon/vgetq_lane_u64
- arm_neon/vmla_n_u32
- arm_neon/vcvtq_f32_s32
- arm_neon/vld1q_u32
- arm_neon/vmax_f32
- armintr/_isunorderedf
- arm_neon/vrshl_u8
- arm_neon/vld4_dup_s64
- arm_neon/vqaddq_u16
- arm_neon/vld4q_lane_f16
- arm_neon/vceqq_p8
- arm_neon/vsubw_u8
- arm_neon/vqmovn_u16
- armintr/_arm_smlsldx
- arm_neon/vcreate_p8
- arm_neon/vqdmull_n_s32
- arm_neon/uint64x2_t
- arm_neon/vmls_s32
- arm_neon/vst3q_f32
- armintr/_arm_bfi
- armintr/_arm_qadd16
- arm_neon/vrshlq_s8
- arm_neon/vget_lane_p16
- arm_neon/vld2_p8
- arm_neon/vld3_lane_u32
- armintr/_MoveFromCoprocessor2
- arm_neon/vqshl_u8
- arm_neon/poly8_t
- arm_neon/vhadd_u16
- arm_neon/vmla_lane_u16
- arm_neon/vshrq_n_u8
- arm_neon/vuzpq_f32
- arm_neon/vmls_lane_f32
- arm_neon/vqneg_s16
- arm_neon/vtrn_p16
- arm_neon/vshrn_n_u32
- arm_neon/vaddhn_u64
- arm_neon/vabal_u32
- arm_neon/vld1q_lane_u32
- arm_neon/vrsraq_n_s32
- arm_neon/vandq_u64
- arm_neon/vqdmull_s32
- arm_neon/vext_s16
- arm_neon/vaddw_s16
- arm_neon/vrev64q_p8
- arm_neon/uint8x8x3_t
- arm_neon/vzip_f32
- armintr/_arm_ssub8
- arm_neon/uint16x4x4_t
- armintr/__swi
- armintr/_arm_smlatb
- arm_neon/vrhaddq_s8
- arm_neon/vpmax_s32
- arm_neon/vqshl_s64
- arm_neon/vrev16q_p8
- arm_neon/vqmovn_u32
- arm_neon/vld1q_f16
- arm_neon/vornq_u64
- arm_neon/vqshlq_n_s16
- arm_neon/vld1_f16
- armintr/_arm_smmlsr
- arm_neon/vshlq_s16
- arm_neon/vsubhn_s16
- arm_neon/vmulq_p8
- arm_neon/vdupq_lane_f32
- armintr/_arm_shadd16
- arm_neon/vornq_s16
- arm_neon/vst1q_lane_u8
- arm_neon/vcaleq_f32
- arm_neon/vst3q_lane_f16
- armintr/_arm_sdiv
- arm_neon/vld2_u16
- arm_neon/vdup_lane_u16
- arm_neon/vst4q_lane_f32
- arm_neon/vdup_n_f32
- arm_neon/vsubq_u8
- arm_neon/vset_lane_p16
- arm_neon/vrsqrte_f32
- arm_neon/vsubl_u8
- arm_neon/vld3q_lane_f32
- arm_neon/vqnegq_s8
- arm_neon/vqmovn_s16
- arm_neon/int16x8x3_t
- arm_neon/veorq_u16
- arm_neon/vqdmulh_n_s16
- arm_neon/vhaddq_u8
- arm_neon/vpadal_u8
- arm_neon/vst2q_s16
- arm_neon/poly16x8x4_t
- arm_neon/int64x2_t
- arm_neon/vmull_s32
- arm_neon/vld4_lane_s32
- arm_neon/vst4q_p8
- arm_neon/vmlal_lane_u16
- arm_neon/vclz_u32
- arm_neon/vsliq_n_s8
- arm_neon/vmls_n_f32
- arm_neon/vmlsl_lane_s16
- arm_neon/vst4q_u32
- arm_neon/vld1q_lane_s16
- arm_neon/vst1q_f32
- arm_neon/vrshr_n_u8
- arm_neon/vst1q_s64
- arm_neon/vbslq_u32
- arm_neon/vset_lane_s8
- arm_neon/vdupq_lane_p16
- arm_neon/vtstq_s16
- arm_neon/vshl_n_s8
- arm_neon/vqrdmulhq_n_s16
- arm_neon/vget_high_f16
- arm_neon/vst4_lane_u32
- arm_neon/vraddhn_s16
- arm_neon/vmlsl_lane_s32
- arm_neon/vld3q_s32
- arm_neon/vsriq_n_u64
- arm_neon/vld4_dup_u8
- arm_neon/vld4q_s8
- arm_neon/vqmovn_s64
- arm_neon/vrev32q_p8
- arm_neon/vsliq_n_p8
- arm_neon/vzipq_s16
- arm_neon/vgetq_lane_s64
- arm_neon/vst4_p16
- arm_neon/vsubq_u16
- arm_neon/vrev64_s32
- armintr/_arm_uhadd8
- arm_neon/vornq_u16
- arm_neon/vst4_lane_s8
- arm_neon/vabd_s32
- arm_neon/vqrdmulhq_s16
- arm_neon/vqshlq_s32
- arm_neon/int64x2x4_t
- arm_neon/vset_lane_u16
- arm_neon/vrsra_n_s32
- arm_neon/vabdl_u16
- arm_neon/vsliq_n_s32
helpviewer_keywords:
- cl.exe compiler, ARM intrinsics
- intrinsics, ARM
- __cps ARM intrinsic
- __dmb ARM intrinsic
- __dsb ARM intrinsic
- __emit ARM intrinsic
- __hvc ARM intrinsic
- __isb ARM intrinsic
- __iso_volatile_load16 ARM intrinsic
- __iso_volatile_load32 ARM intrinsic
- __iso_volatile_load64 ARM intrinsic
- __iso_volatile_load8 ARM intrinsic
- __iso_volatile_store16 ARM intrinsic
- __iso_volatile_store32 ARM intrinsic
- __iso_volatile_store64 ARM intrinsic
- __iso_volatile_store8 ARM intrinsic
- __ldrexd ARM intrinsic
- __prefetch ARM intrinsic
- __rdpmccntr64 ARM intrinsic
- __sev ARM intrinsic
- __static_assert ARM intrinsic
- __swi ARM intrinsic
- __trap ARM intrinsic
- __wfe ARM intrinsic
- __wfi ARM intrinsic
- _AddSatInt ARM intrinsic
- _arm_bfc ARM intrinsic
- _arm_bfi ARM intrinsic
- _arm_clz ARM intrinsic
- _arm_pkhbt ARM intrinsic
- _arm_pkhtb ARM intrinsic
- _arm_qadd ARM intrinsic
- _arm_qadd16 ARM intrinsic
- _arm_qadd8 ARM intrinsic
- _arm_qasx ARM intrinsic
- _arm_qdadd ARM intrinsic
- _arm_qdsub ARM intrinsic
- _arm_qsax ARM intrinsic
- _arm_qsub ARM intrinsic
- _arm_qsub16 ARM intrinsic
- _arm_qsub8 ARM intrinsic
- _arm_rbit ARM intrinsic
- _arm_rev ARM intrinsic
- _arm_rev16 ARM intrinsic
- _arm_revsh ARM intrinsic
- _arm_sadd16 ARM intrinsic
- _arm_sadd8 ARM intrinsic
- _arm_sasx ARM intrinsic
- _arm_sbfx ARM intrinsic
- _arm_sdiv ARM intrinsic
- _arm_shadd16 ARM intrinsic
- _arm_shadd8 ARM intrinsic
- _arm_shasx ARM intrinsic
- _arm_shsax ARM intrinsic
- _arm_shsub16 ARM intrinsic
- _arm_shsub8 ARM intrinsic
- _arm_smlabb ARM intrinsic
- _arm_smlabt ARM intrinsic
- _arm_smlad ARM intrinsic
- _arm_smladx ARM intrinsic
- _arm_smlal ARM intrinsic
- _arm_smlalbb ARM intrinsic
- _arm_smlalbt ARM intrinsic
- _arm_smlald ARM intrinsic
- _arm_smlaldx ARM intrinsic
- _arm_smlaltb ARM intrinsic
- _arm_smlaltt ARM intrinsic
- _arm_smlatb ARM intrinsic
- _arm_smlatt ARM intrinsic
- _arm_smlawb ARM intrinsic
- _arm_smlawt ARM intrinsic
- _arm_smlsd ARM intrinsic
- _arm_smlsdx ARM intrinsic
- _arm_smlsld ARM intrinsic
- _arm_smlsldx ARM intrinsic
- _arm_smmla ARM intrinsic
- _arm_smmlar ARM intrinsic
- _arm_smmls ARM intrinsic
- _arm_smmlsr ARM intrinsic
- _arm_smmul ARM intrinsic
- _arm_smmulr ARM intrinsic
- _arm_smuad ARM intrinsic
- _arm_smuadx ARM intrinsic
- _arm_smulbb ARM intrinsic
- _arm_smulbt ARM intrinsic
- _arm_smull ARM intrinsic
- _arm_smultb ARM intrinsic
- _arm_smultt ARM intrinsic
- _arm_smulwb ARM intrinsic
- _arm_smulwt ARM intrinsic
- _arm_smusd ARM intrinsic
- _arm_smusdx ARM intrinsic
- _arm_ssat ARM intrinsic
- _arm_ssat16 ARM intrinsic
- _arm_ssax ARM intrinsic
- _arm_ssub16 ARM intrinsic
- _arm_ssub8 ARM intrinsic
- _arm_sxtab ARM intrinsic
- _arm_sxtab16 ARM intrinsic
- _arm_sxtah ARM intrinsic
- _arm_sxtb ARM intrinsic
- _arm_sxtb16 ARM intrinsic
- _arm_sxth ARM intrinsic
- _arm_uadd16 ARM intrinsic
- _arm_uadd8 ARM intrinsic
- _arm_uasx ARM intrinsic
- _arm_ubfx ARM intrinsic
- _arm_udiv ARM intrinsic
- _arm_uhadd16 ARM intrinsic
- _arm_uhadd8 ARM intrinsic
- _arm_uhasx ARM intrinsic
- _arm_uhsax ARM intrinsic
- _arm_uhsub16 ARM intrinsic
- _arm_uhsub8 ARM intrinsic
- _arm_umaal ARM intrinsic
- _arm_umlal ARM intrinsic
- _arm_umull ARM intrinsic
- _arm_uqadd16 ARM intrinsic
- _arm_uqadd8 ARM intrinsic
- _arm_uqasx ARM intrinsic
- _arm_uqsax ARM intrinsic
- _arm_uqsub16 ARM intrinsic
- _arm_uqsub8 ARM intrinsic
- _arm_usad8 ARM intrinsic
- _arm_usada8 ARM intrinsic
- _arm_usat ARM intrinsic
- _arm_usat16 ARM intrinsic
- _arm_usax ARM intrinsic
- _arm_usub16 ARM intrinsic
- _arm_usub8 ARM intrinsic
- _arm_uxtab ARM intrinsic
- _arm_uxtab16 ARM intrinsic
- _arm_uxtah ARM intrinsic
- _arm_uxtb ARM intrinsic
- _arm_uxtb16 ARM intrinsic
- _arm_uxth ARM intrinsic
- _CopyDoubleFromInt64 ARM intrinsic
- _CopyFloatFromInt32 ARM intrinsic
- _CopyInt32FromFloat ARM intrinsic
- _CopyInt64FromDouble ARM intrinsic
- _CountLeadingOnes ARM intrinsic
- _CountLeadingOnes64 ARM intrinsic
- _CountLeadingSigns ARM intrinsic
- _CountLeadingSigns64 ARM intrinsic
- _CountLeadingZeros ARM intrinsic
- _CountLeadingZeros64 ARM intrinsic
- _CountOneBits ARM intrinsic
- _CountOneBits64 ARM intrinsic
- _DAddSatInt ARM intrinsic
- _DSubSatInt ARM intrinsic
- _isunordered ARM intrinsic
- _isunorderedf ARM intrinsic
- _MoveFromCoprocessor ARM intrinsic
- _MoveFromCoprocessor2 ARM intrinsic
- _MoveFromCoprocessor64 ARM intrinsic
- _MoveToCoprocessor ARM intrinsic
- _MoveToCoprocessor2 ARM intrinsic
- _MoveToCoprocessor64 ARM intrinsic
- _MulHigh ARM intrinsic
- _MulUnsignedHigh ARM intrinsic
- _ReadBankedReg ARM intrinsic
- _ReadStatusReg ARM intrinsic
- _SubSatInt ARM intrinsic
- _WriteBankedReg ARM intrinsic
- _WriteStatusReg ARM intrinsic
- float32x2_t ARM intrinsic
- float32x2x2_t ARM intrinsic
- float32x2x3_t ARM intrinsic
- float32x2x4_t ARM intrinsic
- float32x4_t ARM intrinsic
- float32x4x2_t ARM intrinsic
- float32x4x3_t ARM intrinsic
- float32x4x4_t ARM intrinsic
- int16x4_t ARM intrinsic
- int16x4x2_t ARM intrinsic
- int16x4x3_t ARM intrinsic
- int16x4x4_t ARM intrinsic
- int16x8_t ARM intrinsic
- int16x8x2_t ARM intrinsic
- int16x8x3_t ARM intrinsic
- int16x8x4_t ARM intrinsic
- int32x2_t ARM intrinsic
- int32x2x2_t ARM intrinsic
- int32x2x3_t ARM intrinsic
- int32x2x4_t ARM intrinsic
- int32x4_t ARM intrinsic
- int32x4x2_t ARM intrinsic
- int32x4x3_t ARM intrinsic
- int32x4x4_t ARM intrinsic
- int64x1_t ARM intrinsic
- int64x1x2_t ARM intrinsic
- int64x1x3_t ARM intrinsic
- int64x1x4_t ARM intrinsic
- int64x2_t ARM intrinsic
- int64x2x2_t ARM intrinsic
- int64x2x3_t ARM intrinsic
- int64x2x4_t ARM intrinsic
- int8x16_t ARM intrinsic
- int8x16x2_t ARM intrinsic
- int8x16x3_t ARM intrinsic
- int8x16x4_t ARM intrinsic
- int8x8_t ARM intrinsic
- int8x8x2_t ARM intrinsic
- int8x8x3_t ARM intrinsic
- int8x8x4_t ARM intrinsic
- poly16_t ARM intrinsic
- poly16x4_t ARM intrinsic
- poly16x4x2_t ARM intrinsic
- poly16x4x3_t ARM intrinsic
- poly16x4x4_t ARM intrinsic
- poly16x8_t ARM intrinsic
- poly16x8x2_t ARM intrinsic
- poly16x8x3_t ARM intrinsic
- poly16x8x4_t ARM intrinsic
- poly8_t ARM intrinsic
- poly8x16_t ARM intrinsic
- poly8x16x2_t ARM intrinsic
- poly8x16x3_t ARM intrinsic
- poly8x16x4_t ARM intrinsic
- poly8x8_t ARM intrinsic
- poly8x8x2_t ARM intrinsic
- poly8x8x3_t ARM intrinsic
- poly8x8x4_t ARM intrinsic
- uint16x4_t ARM intrinsic
- uint16x4x2_t ARM intrinsic
- uint16x4x3_t ARM intrinsic
- uint16x4x4_t ARM intrinsic
- uint16x8_t ARM intrinsic
- uint16x8x2_t ARM intrinsic
- uint16x8x3_t ARM intrinsic
- uint16x8x4_t ARM intrinsic
- uint32x2_t ARM intrinsic
- uint32x2x2_t ARM intrinsic
- uint32x2x3_t ARM intrinsic
- uint32x2x4_t ARM intrinsic
- uint32x4_t ARM intrinsic
- uint32x4x2_t ARM intrinsic
- uint32x4x3_t ARM intrinsic
- uint32x4x4_t ARM intrinsic
- uint64x1_t ARM intrinsic
- uint64x1x2_t ARM intrinsic
- uint64x1x3_t ARM intrinsic
- uint64x1x4_t ARM intrinsic
- uint64x2_t ARM intrinsic
- uint64x2x2_t ARM intrinsic
- uint64x2x3_t ARM intrinsic
- uint64x2x4_t ARM intrinsic
- uint8x16_t ARM intrinsic
- uint8x16x2_t ARM intrinsic
- uint8x16x3_t ARM intrinsic
- uint8x16x4_t ARM intrinsic
- uint8x8_t ARM intrinsic
- uint8x8x2_t ARM intrinsic
- uint8x8x3_t ARM intrinsic
- uint8x8x4_t ARM intrinsic
- vaba_s16 ARM intrinsic
- vaba_s32 ARM intrinsic
- vaba_s8 ARM intrinsic
- vaba_u16 ARM intrinsic
- vaba_u32 ARM intrinsic
- vaba_u8 ARM intrinsic
- vabal_s16 ARM intrinsic
- vabal_s32 ARM intrinsic
- vabal_s8 ARM intrinsic
- vabal_u16 ARM intrinsic
- vabal_u32 ARM intrinsic
- vabal_u8 ARM intrinsic
- vabaq_s16 ARM intrinsic
- vabaq_s32 ARM intrinsic
- vabaq_s8 ARM intrinsic
- vabaq_u16 ARM intrinsic
- vabaq_u32 ARM intrinsic
- vabaq_u8 ARM intrinsic
- vabd_f32 ARM intrinsic
- vabd_s16 ARM intrinsic
- vabd_s32 ARM intrinsic
- vabd_s8 ARM intrinsic
- vabd_u16 ARM intrinsic
- vabd_u32 ARM intrinsic
- vabd_u8 ARM intrinsic
- vabdl_s16 ARM intrinsic
- vabdl_s32 ARM intrinsic
- vabdl_s8 ARM intrinsic
- vabdl_u16 ARM intrinsic
- vabdl_u32 ARM intrinsic
- vabdl_u8 ARM intrinsic
- vabdq_f32 ARM intrinsic
- vabdq_s16 ARM intrinsic
- vabdq_s32 ARM intrinsic
- vabdq_s8 ARM intrinsic
- vabdq_u16 ARM intrinsic
- vabdq_u32 ARM intrinsic
- vabdq_u8 ARM intrinsic
- vabs_f32 ARM intrinsic
- vabs_s16 ARM intrinsic
- vabs_s32 ARM intrinsic
- vabs_s8 ARM intrinsic
- vabsq_f32 ARM intrinsic
- vabsq_s16 ARM intrinsic
- vabsq_s32 ARM intrinsic
- vabsq_s8 ARM intrinsic
- vadd_f32 ARM intrinsic
- vadd_s16 ARM intrinsic
- vadd_s32 ARM intrinsic
- vadd_s64 ARM intrinsic
- vadd_s8 ARM intrinsic
- vadd_u16 ARM intrinsic
- vadd_u32 ARM intrinsic
- vadd_u64 ARM intrinsic
- vadd_u8 ARM intrinsic
- vaddhn_s16 ARM intrinsic
- vaddhn_s32 ARM intrinsic
- vaddhn_s64 ARM intrinsic
- vaddhn_u16 ARM intrinsic
- vaddhn_u32 ARM intrinsic
- vaddhn_u64 ARM intrinsic
- vaddl_s16 ARM intrinsic
- vaddl_s32 ARM intrinsic
- vaddl_s8 ARM intrinsic
- vaddl_u16 ARM intrinsic
- vaddl_u32 ARM intrinsic
- vaddl_u8 ARM intrinsic
- vaddq_f32 ARM intrinsic
- vaddq_s16 ARM intrinsic
- vaddq_s32 ARM intrinsic
- vaddq_s64 ARM intrinsic
- vaddq_s8 ARM intrinsic
- vaddq_u16 ARM intrinsic
- vaddq_u32 ARM intrinsic
- vaddq_u64 ARM intrinsic
- vaddq_u8 ARM intrinsic
- vaddw_s16 ARM intrinsic
- vaddw_s32 ARM intrinsic
- vaddw_s8 ARM intrinsic
- vaddw_u16 ARM intrinsic
- vaddw_u32 ARM intrinsic
- vaddw_u8 ARM intrinsic
- vand_s16 ARM intrinsic
- vand_s32 ARM intrinsic
- vand_s64 ARM intrinsic
- vand_s8 ARM intrinsic
- vand_u16 ARM intrinsic
- vand_u32 ARM intrinsic
- vand_u64 ARM intrinsic
- vand_u8 ARM intrinsic
- vandq_s16 ARM intrinsic
- vandq_s32 ARM intrinsic
- vandq_s64 ARM intrinsic
- vandq_s8 ARM intrinsic
- vandq_u16 ARM intrinsic
- vandq_u32 ARM intrinsic
- vandq_u64 ARM intrinsic
- vandq_u8 ARM intrinsic
- vbic_s16 ARM intrinsic
- vbic_s32 ARM intrinsic
- vbic_s64 ARM intrinsic
- vbic_s8 ARM intrinsic
- vbic_u16 ARM intrinsic
- vbic_u32 ARM intrinsic
- vbic_u64 ARM intrinsic
- vbic_u8 ARM intrinsic
- vbicq_s16 ARM intrinsic
- vbicq_s32 ARM intrinsic
- vbicq_s64 ARM intrinsic
- vbicq_s8 ARM intrinsic
- vbicq_u16 ARM intrinsic
- vbicq_u32 ARM intrinsic
- vbicq_u64 ARM intrinsic
- vbicq_u8 ARM intrinsic
- vbsl_f32 ARM intrinsic
- vbsl_p16 ARM intrinsic
- vbsl_p8 ARM intrinsic
- vbsl_s16 ARM intrinsic
- vbsl_s32 ARM intrinsic
- vbsl_s64 ARM intrinsic
- vbsl_s8 ARM intrinsic
- vbsl_u16 ARM intrinsic
- vbsl_u32 ARM intrinsic
- vbsl_u64 ARM intrinsic
- vbsl_u8 ARM intrinsic
- vbslq_f32 ARM intrinsic
- vbslq_p16 ARM intrinsic
- vbslq_p8 ARM intrinsic
- vbslq_s16 ARM intrinsic
- vbslq_s32 ARM intrinsic
- vbslq_s64 ARM intrinsic
- vbslq_s8 ARM intrinsic
- vbslq_u16 ARM intrinsic
- vbslq_u32 ARM intrinsic
- vbslq_u64 ARM intrinsic
- vbslq_u8 ARM intrinsic
- vcage_f32 ARM intrinsic
- vcageq_f32 ARM intrinsic
- vcagt_f32 ARM intrinsic
- vcagtq_f32 ARM intrinsic
- vcale_f32 ARM intrinsic
- vcaleq_f32 ARM intrinsic
- vcalt_f32 ARM intrinsic
- vcaltq_f32 ARM intrinsic
- vceq_f32 ARM intrinsic
- vceq_p8 ARM intrinsic
- vceq_s16 ARM intrinsic
- vceq_s32 ARM intrinsic
- vceq_s8 ARM intrinsic
- vceq_u16 ARM intrinsic
- vceq_u32 ARM intrinsic
- vceq_u8 ARM intrinsic
- vceqq_f32 ARM intrinsic
- vceqq_p8 ARM intrinsic
- vceqq_s16 ARM intrinsic
- vceqq_s32 ARM intrinsic
- vceqq_s8 ARM intrinsic
- vceqq_u16 ARM intrinsic
- vceqq_u32 ARM intrinsic
- vceqq_u8 ARM intrinsic
- vcge_f32 ARM intrinsic
- vcge_s16 ARM intrinsic
- vcge_s32 ARM intrinsic
- vcge_s8 ARM intrinsic
- vcge_u16 ARM intrinsic
- vcge_u32 ARM intrinsic
- vcge_u8 ARM intrinsic
- vcgeq_f32 ARM intrinsic
- vcgeq_s16 ARM intrinsic
- vcgeq_s32 ARM intrinsic
- vcgeq_s8 ARM intrinsic
- vcgeq_u16 ARM intrinsic
- vcgeq_u32 ARM intrinsic
- vcgeq_u8 ARM intrinsic
- vcgt_f32 ARM intrinsic
- vcgt_s16 ARM intrinsic
- vcgt_s32 ARM intrinsic
- vcgt_s8 ARM intrinsic
- vcgt_u16 ARM intrinsic
- vcgt_u32 ARM intrinsic
- vcgt_u8 ARM intrinsic
- vcgtq_f32 ARM intrinsic
- vcgtq_s16 ARM intrinsic
- vcgtq_s32 ARM intrinsic
- vcgtq_s8 ARM intrinsic
- vcgtq_u16 ARM intrinsic
- vcgtq_u32 ARM intrinsic
- vcgtq_u8 ARM intrinsic
- vcle_f32 ARM intrinsic
- vcle_s16 ARM intrinsic
- vcle_s32 ARM intrinsic
- vcle_s8 ARM intrinsic
- vcle_u16 ARM intrinsic
- vcle_u32 ARM intrinsic
- vcle_u8 ARM intrinsic
- vcleq_f32 ARM intrinsic
- vcleq_s16 ARM intrinsic
- vcleq_s32 ARM intrinsic
- vcleq_s8 ARM intrinsic
- vcleq_u16 ARM intrinsic
- vcleq_u32 ARM intrinsic
- vcleq_u8 ARM intrinsic
- vcls_s16 ARM intrinsic
- vcls_s32 ARM intrinsic
- vcls_s8 ARM intrinsic
- vclsq_s16 ARM intrinsic
- vclsq_s32 ARM intrinsic
- vclsq_s8 ARM intrinsic
- vclt_f32 ARM intrinsic
- vclt_s16 ARM intrinsic
- vclt_s32 ARM intrinsic
- vclt_s8 ARM intrinsic
- vclt_u16 ARM intrinsic
- vclt_u32 ARM intrinsic
- vclt_u8 ARM intrinsic
- vcltq_f32 ARM intrinsic
- vcltq_s16 ARM intrinsic
- vcltq_s32 ARM intrinsic
- vcltq_s8 ARM intrinsic
- vcltq_u16 ARM intrinsic
- vcltq_u32 ARM intrinsic
- vcltq_u8 ARM intrinsic
- vclz_s16 ARM intrinsic
- vclz_s32 ARM intrinsic
- vclz_s8 ARM intrinsic
- vclz_u16 ARM intrinsic
- vclz_u32 ARM intrinsic
- vclz_u8 ARM intrinsic
- vclzq_s16 ARM intrinsic
- vclzq_s32 ARM intrinsic
- vclzq_s8 ARM intrinsic
- vclzq_u16 ARM intrinsic
- vclzq_u32 ARM intrinsic
- vclzq_u8 ARM intrinsic
- vcnt_p8 ARM intrinsic
- vcnt_s8 ARM intrinsic
- vcnt_u8 ARM intrinsic
- vcntq_p8 ARM intrinsic
- vcntq_s8 ARM intrinsic
- vcntq_u8 ARM intrinsic
- vcombine_f16 ARM intrinsic
- vcombine_f32 ARM intrinsic
- vcombine_p16 ARM intrinsic
- vcombine_p8 ARM intrinsic
- vcombine_s16 ARM intrinsic
- vcombine_s32 ARM intrinsic
- vcombine_s64 ARM intrinsic
- vcombine_s8 ARM intrinsic
- vcombine_u16 ARM intrinsic
- vcombine_u32 ARM intrinsic
- vcombine_u64 ARM intrinsic
- vcombine_u8 ARM intrinsic
- vcreate_f16 ARM intrinsic
- vcreate_f32 ARM intrinsic
- vcreate_p16 ARM intrinsic
- vcreate_p8 ARM intrinsic
- vcreate_s16 ARM intrinsic
- vcreate_s32 ARM intrinsic
- vcreate_s64 ARM intrinsic
- vcreate_s8 ARM intrinsic
- vcreate_u16 ARM intrinsic
- vcreate_u32 ARM intrinsic
- vcreate_u64 ARM intrinsic
- vcreate_u8 ARM intrinsic
- vcvt_f16_f32 ARM intrinsic
- vcvt_f32_f16 ARM intrinsic
- vcvt_f32_s32 ARM intrinsic
- vcvt_f32_u32 ARM intrinsic
- vcvt_n_f32_s32 ARM intrinsic
- vcvt_n_f32_u32 ARM intrinsic
- vcvt_n_s32_f32 ARM intrinsic
- vcvt_n_u32_f32 ARM intrinsic
- vcvt_s32_f32 ARM intrinsic
- vcvt_u32_f32 ARM intrinsic
- vcvtq_f32_s32 ARM intrinsic
- vcvtq_f32_u32 ARM intrinsic
- vcvtq_n_f32_s32 ARM intrinsic
- vcvtq_n_f32_u32 ARM intrinsic
- vcvtq_n_s32_f32 ARM intrinsic
- vcvtq_n_u32_f32 ARM intrinsic
- vcvtq_s32_f32 ARM intrinsic
- vcvtq_u32_f32 ARM intrinsic
- vdup_lane_f32 ARM intrinsic
- vdup_lane_p16 ARM intrinsic
- vdup_lane_p8 ARM intrinsic
- vdup_lane_s16 ARM intrinsic
- vdup_lane_s32 ARM intrinsic
- vdup_lane_s64 ARM intrinsic
- vdup_lane_s8 ARM intrinsic
- vdup_lane_u16 ARM intrinsic
- vdup_lane_u32 ARM intrinsic
- vdup_lane_u64 ARM intrinsic
- vdup_lane_u8 ARM intrinsic
- vdup_n_f32 ARM intrinsic
- vdup_n_p16 ARM intrinsic
- vdup_n_p8 ARM intrinsic
- vdup_n_s16 ARM intrinsic
- vdup_n_s32 ARM intrinsic
- vdup_n_s64 ARM intrinsic
- vdup_n_s8 ARM intrinsic
- vdup_n_u16 ARM intrinsic
- vdup_n_u32 ARM intrinsic
- vdup_n_u64 ARM intrinsic
- vdup_n_u8 ARM intrinsic
- vdupq_lane_f32 ARM intrinsic
- vdupq_lane_p16 ARM intrinsic
- vdupq_lane_p8 ARM intrinsic
- vdupq_lane_s16 ARM intrinsic
- vdupq_lane_s32 ARM intrinsic
- vdupq_lane_s64 ARM intrinsic
- vdupq_lane_s8 ARM intrinsic
- vdupq_lane_u16 ARM intrinsic
- vdupq_lane_u32 ARM intrinsic
- vdupq_lane_u64 ARM intrinsic
- vdupq_lane_u8 ARM intrinsic
- vdupq_n_f32 ARM intrinsic
- vdupq_n_p16 ARM intrinsic
- vdupq_n_p8 ARM intrinsic
- vdupq_n_s16 ARM intrinsic
- vdupq_n_s32 ARM intrinsic
- vdupq_n_s64 ARM intrinsic
- vdupq_n_s8 ARM intrinsic
- vdupq_n_u16 ARM intrinsic
- vdupq_n_u32 ARM intrinsic
- vdupq_n_u64 ARM intrinsic
- vdupq_n_u8 ARM intrinsic
- veor_s16 ARM intrinsic
- veor_s32 ARM intrinsic
- veor_s64 ARM intrinsic
- veor_s8 ARM intrinsic
- veor_u16 ARM intrinsic
- veor_u32 ARM intrinsic
- veor_u64 ARM intrinsic
- veor_u8 ARM intrinsic
- veorq_s16 ARM intrinsic
- veorq_s32 ARM intrinsic
- veorq_s64 ARM intrinsic
- veorq_s8 ARM intrinsic
- veorq_u16 ARM intrinsic
- veorq_u32 ARM intrinsic
- veorq_u64 ARM intrinsic
- veorq_u8 ARM intrinsic
- vext_p16 ARM intrinsic
- vext_p8 ARM intrinsic
- vext_s16 ARM intrinsic
- vext_s32 ARM intrinsic
- vext_s64 ARM intrinsic
- vext_s8 ARM intrinsic
- vext_u16 ARM intrinsic
- vext_u32 ARM intrinsic
- vext_u64 ARM intrinsic
- vext_u8 ARM intrinsic
- vextq_p16 ARM intrinsic
- vextq_p8 ARM intrinsic
- vextq_s16 ARM intrinsic
- vextq_s32 ARM intrinsic
- vextq_s64 ARM intrinsic
- vextq_s8 ARM intrinsic
- vextq_u16 ARM intrinsic
- vextq_u32 ARM intrinsic
- vextq_u64 ARM intrinsic
- vextq_u8 ARM intrinsic
- vget_high_f16 ARM intrinsic
- vget_high_f32 ARM intrinsic
- vget_high_p16 ARM intrinsic
- vget_high_p8 ARM intrinsic
- vget_high_s16 ARM intrinsic
- vget_high_s32 ARM intrinsic
- vget_high_s64 ARM intrinsic
- vget_high_s8 ARM intrinsic
- vget_high_u16 ARM intrinsic
- vget_high_u32 ARM intrinsic
- vget_high_u64 ARM intrinsic
- vget_high_u8 ARM intrinsic
- vget_lane_f32 ARM intrinsic
- vget_lane_p16 ARM intrinsic
- vget_lane_p8 ARM intrinsic
- vget_lane_s16 ARM intrinsic
- vget_lane_s32 ARM intrinsic
- vget_lane_s64 ARM intrinsic
- vget_lane_s8 ARM intrinsic
- vget_lane_u16 ARM intrinsic
- vget_lane_u32 ARM intrinsic
- vget_lane_u64 ARM intrinsic
- vget_lane_u8 ARM intrinsic
- vget_low_f16 ARM intrinsic
- vget_low_f32 ARM intrinsic
- vget_low_p16 ARM intrinsic
- vget_low_p8 ARM intrinsic
- vget_low_s16 ARM intrinsic
- vget_low_s32 ARM intrinsic
- vget_low_s64 ARM intrinsic
- vget_low_s8 ARM intrinsic
- vget_low_u16 ARM intrinsic
- vget_low_u32 ARM intrinsic
- vget_low_u64 ARM intrinsic
- vget_low_u8 ARM intrinsic
- vgetq_lane_f32 ARM intrinsic
- vgetq_lane_p16 ARM intrinsic
- vgetq_lane_p8 ARM intrinsic
- vgetq_lane_s16 ARM intrinsic
- vgetq_lane_s32 ARM intrinsic
- vgetq_lane_s64 ARM intrinsic
- vgetq_lane_s8 ARM intrinsic
- vgetq_lane_u16 ARM intrinsic
- vgetq_lane_u32 ARM intrinsic
- vgetq_lane_u64 ARM intrinsic
- vgetq_lane_u8 ARM intrinsic
- vhadd_s16 ARM intrinsic
- vhadd_s32 ARM intrinsic
- vhadd_s8 ARM intrinsic
- vhadd_u16 ARM intrinsic
- vhadd_u32 ARM intrinsic
- vhadd_u8 ARM intrinsic
- vhaddq_s16 ARM intrinsic
- vhaddq_s32 ARM intrinsic
- vhaddq_s8 ARM intrinsic
- vhaddq_u16 ARM intrinsic
- vhaddq_u32 ARM intrinsic
- vhaddq_u8 ARM intrinsic
- vhsub_s16 ARM intrinsic
- vhsub_s32 ARM intrinsic
- vhsub_s8 ARM intrinsic
- vhsub_u16 ARM intrinsic
- vhsub_u32 ARM intrinsic
- vhsub_u8 ARM intrinsic
- vhsubq_s16 ARM intrinsic
- vhsubq_s32 ARM intrinsic
- vhsubq_s8 ARM intrinsic
- vhsubq_u16 ARM intrinsic
- vhsubq_u32 ARM intrinsic
- vhsubq_u8 ARM intrinsic
- vld1_dup_f16 ARM intrinsic
- vld1_dup_f32 ARM intrinsic
- vld1_dup_p16 ARM intrinsic
- vld1_dup_p8 ARM intrinsic
- vld1_dup_s16 ARM intrinsic
- vld1_dup_s32 ARM intrinsic
- vld1_dup_s64 ARM intrinsic
- vld1_dup_s8 ARM intrinsic
- vld1_dup_u16 ARM intrinsic
- vld1_dup_u32 ARM intrinsic
- vld1_dup_u64 ARM intrinsic
- vld1_dup_u8 ARM intrinsic
- vld1_f16 ARM intrinsic
- vld1_f32 ARM intrinsic
- vld1_lane_f32 ARM intrinsic
- vld1_lane_p16 ARM intrinsic
- vld1_lane_p8 ARM intrinsic
- vld1_lane_s16 ARM intrinsic
- vld1_lane_s32 ARM intrinsic
- vld1_lane_s64 ARM intrinsic
- vld1_lane_s8 ARM intrinsic
- vld1_lane_u16 ARM intrinsic
- vld1_lane_u32 ARM intrinsic
- vld1_lane_u64 ARM intrinsic
- vld1_lane_u8 ARM intrinsic
- vld1_p16 ARM intrinsic
- vld1_p8 ARM intrinsic
- vld1_s16 ARM intrinsic
- vld1_s32 ARM intrinsic
- vld1_s64 ARM intrinsic
- vld1_s8 ARM intrinsic
- vld1_u16 ARM intrinsic
- vld1_u32 ARM intrinsic
- vld1_u64 ARM intrinsic
- vld1_u8 ARM intrinsic
- vld1q_dup_f16 ARM intrinsic
- vld1q_dup_f32 ARM intrinsic
- vld1q_dup_p16 ARM intrinsic
- vld1q_dup_p8 ARM intrinsic
- vld1q_dup_s16 ARM intrinsic
- vld1q_dup_s32 ARM intrinsic
- vld1q_dup_s64 ARM intrinsic
- vld1q_dup_s8 ARM intrinsic
- vld1q_dup_u16 ARM intrinsic
- vld1q_dup_u32 ARM intrinsic
- vld1q_dup_u64 ARM intrinsic
- vld1q_dup_u8 ARM intrinsic
- vld1q_f16 ARM intrinsic
- vld1q_f32 ARM intrinsic
- vld1q_lane_f16 ARM intrinsic
- vld1q_lane_f32 ARM intrinsic
- vld1q_lane_p16 ARM intrinsic
- vld1q_lane_p8 ARM intrinsic
- vld1q_lane_s16 ARM intrinsic
- vld1q_lane_s32 ARM intrinsic
- vld1q_lane_s64 ARM intrinsic
- vld1q_lane_s8 ARM intrinsic
- vld1q_lane_u16 ARM intrinsic
- vld1q_lane_u32 ARM intrinsic
- vld1q_lane_u64 ARM intrinsic
- vld1q_lane_u8 ARM intrinsic
- vld1q_p16 ARM intrinsic
- vld1q_p8 ARM intrinsic
- vld1q_s16 ARM intrinsic
- vld1q_s32 ARM intrinsic
- vld1q_s64 ARM intrinsic
- vld1q_s8 ARM intrinsic
- vld1q_u16 ARM intrinsic
- vld1q_u32 ARM intrinsic
- vld1q_u64 ARM intrinsic
- vld1q_u8 ARM intrinsic
- vld2_dup_f16 ARM intrinsic
- vld2_dup_f32 ARM intrinsic
- vld2_dup_p16 ARM intrinsic
- vld2_dup_p8 ARM intrinsic
- vld2_dup_s16 ARM intrinsic
- vld2_dup_s32 ARM intrinsic
- vld2_dup_s64 ARM intrinsic
- vld2_dup_s8 ARM intrinsic
- vld2_dup_u16 ARM intrinsic
- vld2_dup_u32 ARM intrinsic
- vld2_dup_u64 ARM intrinsic
- vld2_dup_u8 ARM intrinsic
- vld2_f16 ARM intrinsic
- vld2_f32 ARM intrinsic
- vld2_lane_f16 ARM intrinsic
- vld2_lane_f32 ARM intrinsic
- vld2_lane_p16 ARM intrinsic
- vld2_lane_p8 ARM intrinsic
- vld2_lane_s16 ARM intrinsic
- vld2_lane_s32 ARM intrinsic
- vld2_lane_s8 ARM intrinsic
- vld2_lane_u16 ARM intrinsic
- vld2_lane_u32 ARM intrinsic
- vld2_lane_u8 ARM intrinsic
- vld2_p16 ARM intrinsic
- vld2_p8 ARM intrinsic
- vld2_s16 ARM intrinsic
- vld2_s32 ARM intrinsic
- vld2_s64 ARM intrinsic
- vld2_s8 ARM intrinsic
- vld2_u16 ARM intrinsic
- vld2_u32 ARM intrinsic
- vld2_u64 ARM intrinsic
- vld2_u8 ARM intrinsic
- vld2q_f16 ARM intrinsic
- vld2q_f32 ARM intrinsic
- vld2q_lane_f16 ARM intrinsic
- vld2q_lane_f32 ARM intrinsic
- vld2q_lane_p16 ARM intrinsic
- vld2q_lane_s16 ARM intrinsic
- vld2q_lane_s32 ARM intrinsic
- vld2q_lane_u16 ARM intrinsic
- vld2q_lane_u32 ARM intrinsic
- vld2q_p16 ARM intrinsic
- vld2q_p8 ARM intrinsic
- vld2q_s16 ARM intrinsic
- vld2q_s32 ARM intrinsic
- vld2q_s8 ARM intrinsic
- vld2q_u16 ARM intrinsic
- vld2q_u32 ARM intrinsic
- vld2q_u8 ARM intrinsic
- vld3_dup_f16 ARM intrinsic
- vld3_dup_f32 ARM intrinsic
- vld3_dup_p16 ARM intrinsic
- vld3_dup_p8 ARM intrinsic
- vld3_dup_s16 ARM intrinsic
- vld3_dup_s32 ARM intrinsic
- vld3_dup_s64 ARM intrinsic
- vld3_dup_s8 ARM intrinsic
- vld3_dup_u16 ARM intrinsic
- vld3_dup_u32 ARM intrinsic
- vld3_dup_u64 ARM intrinsic
- vld3_dup_u8 ARM intrinsic
- vld3_f16 ARM intrinsic
- vld3_f32 ARM intrinsic
- vld3_lane_f16 ARM intrinsic
- vld3_lane_f32 ARM intrinsic
- vld3_lane_p16 ARM intrinsic
- vld3_lane_p8 ARM intrinsic
- vld3_lane_s16 ARM intrinsic
- vld3_lane_s32 ARM intrinsic
- vld3_lane_s8 ARM intrinsic
- vld3_lane_u16 ARM intrinsic
- vld3_lane_u32 ARM intrinsic
- vld3_lane_u8 ARM intrinsic
- vld3_p16 ARM intrinsic
- vld3_p8 ARM intrinsic
- vld3_s16 ARM intrinsic
- vld3_s32 ARM intrinsic
- vld3_s64 ARM intrinsic
- vld3_s8 ARM intrinsic
- vld3_u16 ARM intrinsic
- vld3_u32 ARM intrinsic
- vld3_u64 ARM intrinsic
- vld3_u8 ARM intrinsic
- vld3q_f16 ARM intrinsic
- vld3q_f32 ARM intrinsic
- vld3q_lane_f16 ARM intrinsic
- vld3q_lane_f32 ARM intrinsic
- vld3q_lane_p16 ARM intrinsic
- vld3q_lane_s16 ARM intrinsic
- vld3q_lane_s32 ARM intrinsic
- vld3q_lane_u16 ARM intrinsic
- vld3q_lane_u32 ARM intrinsic
- vld3q_p16 ARM intrinsic
- vld3q_p8 ARM intrinsic
- vld3q_s16 ARM intrinsic
- vld3q_s32 ARM intrinsic
- vld3q_s8 ARM intrinsic
- vld3q_u16 ARM intrinsic
- vld3q_u32 ARM intrinsic
- vld3q_u8 ARM intrinsic
- vld4_dup_f16 ARM intrinsic
- vld4_dup_f32 ARM intrinsic
- vld4_dup_p16 ARM intrinsic
- vld4_dup_p8 ARM intrinsic
- vld4_dup_s16 ARM intrinsic
- vld4_dup_s32 ARM intrinsic
- vld4_dup_s64 ARM intrinsic
- vld4_dup_s8 ARM intrinsic
- vld4_dup_u16 ARM intrinsic
- vld4_dup_u32 ARM intrinsic
- vld4_dup_u64 ARM intrinsic
- vld4_dup_u8 ARM intrinsic
- vld4_f16 ARM intrinsic
- vld4_f32 ARM intrinsic
- vld4_lane_f16 ARM intrinsic
- vld4_lane_f32 ARM intrinsic
- vld4_lane_p16 ARM intrinsic
- vld4_lane_p8 ARM intrinsic
- vld4_lane_s16 ARM intrinsic
- vld4_lane_s32 ARM intrinsic
- vld4_lane_s8 ARM intrinsic
- vld4_lane_u16 ARM intrinsic
- vld4_lane_u32 ARM intrinsic
- vld4_lane_u8 ARM intrinsic
- vld4_p16 ARM intrinsic
- vld4_p8 ARM intrinsic
- vld4_s16 ARM intrinsic
- vld4_s32 ARM intrinsic
- vld4_s64 ARM intrinsic
- vld4_s8 ARM intrinsic
- vld4_u16 ARM intrinsic
- vld4_u32 ARM intrinsic
- vld4_u64 ARM intrinsic
- vld4_u8 ARM intrinsic
- vld4q_f16 ARM intrinsic
- vld4q_f32 ARM intrinsic
- vld4q_lane_f16 ARM intrinsic
- vld4q_lane_f32 ARM intrinsic
- vld4q_lane_p16 ARM intrinsic
- vld4q_lane_s16 ARM intrinsic
- vld4q_lane_s32 ARM intrinsic
- vld4q_lane_u16 ARM intrinsic
- vld4q_lane_u32 ARM intrinsic
- vld4q_p16 ARM intrinsic
- vld4q_p8 ARM intrinsic
- vld4q_s16 ARM intrinsic
- vld4q_s32 ARM intrinsic
- vld4q_s8 ARM intrinsic
- vld4q_u16 ARM intrinsic
- vld4q_u32 ARM intrinsic
- vld4q_u8 ARM intrinsic
- vmax_f32 ARM intrinsic
- vmax_s16 ARM intrinsic
- vmax_s32 ARM intrinsic
- vmax_s8 ARM intrinsic
- vmax_u16 ARM intrinsic
- vmax_u32 ARM intrinsic
- vmax_u8 ARM intrinsic
- vmaxq_f32 ARM intrinsic
- vmaxq_s16 ARM intrinsic
- vmaxq_s32 ARM intrinsic
- vmaxq_s8 ARM intrinsic
- vmaxq_u16 ARM intrinsic
- vmaxq_u32 ARM intrinsic
- vmaxq_u8 ARM intrinsic
- vmin_f32 ARM intrinsic
- vmin_s16 ARM intrinsic
- vmin_s32 ARM intrinsic
- vmin_s8 ARM intrinsic
- vmin_u16 ARM intrinsic
- vmin_u32 ARM intrinsic
- vmin_u8 ARM intrinsic
- vminq_f32 ARM intrinsic
- vminq_s16 ARM intrinsic
- vminq_s32 ARM intrinsic
- vminq_s8 ARM intrinsic
- vminq_u16 ARM intrinsic
- vminq_u32 ARM intrinsic
- vminq_u8 ARM intrinsic
- vmla_f32 ARM intrinsic
- vmla_lane_f32 ARM intrinsic
- vmla_lane_s16 ARM intrinsic
- vmla_lane_s32 ARM intrinsic
- vmla_lane_u16 ARM intrinsic
- vmla_lane_u32 ARM intrinsic
- vmla_n_f32 ARM intrinsic
- vmla_n_s16 ARM intrinsic
- vmla_n_s32 ARM intrinsic
- vmla_n_u16 ARM intrinsic
- vmla_n_u32 ARM intrinsic
- vmla_s16 ARM intrinsic
- vmla_s32 ARM intrinsic
- vmla_s8 ARM intrinsic
- vmla_u16 ARM intrinsic
- vmla_u32 ARM intrinsic
- vmla_u8 ARM intrinsic
- vmlal_lane_s16 ARM intrinsic
- vmlal_lane_s32 ARM intrinsic
- vmlal_lane_u16 ARM intrinsic
- vmlal_lane_u32 ARM intrinsic
- vmlal_n_s16 ARM intrinsic
- vmlal_n_s32 ARM intrinsic
- vmlal_n_u16 ARM intrinsic
- vmlal_n_u32 ARM intrinsic
- vmlal_s16 ARM intrinsic
- vmlal_s32 ARM intrinsic
- vmlal_s8 ARM intrinsic
- vmlal_u16 ARM intrinsic
- vmlal_u32 ARM intrinsic
- vmlal_u8 ARM intrinsic
- vmlaq_f32 ARM intrinsic
- vmlaq_lane_f32 ARM intrinsic
- vmlaq_lane_s16 ARM intrinsic
- vmlaq_lane_s32 ARM intrinsic
- vmlaq_lane_u16 ARM intrinsic
- vmlaq_lane_u32 ARM intrinsic
- vmlaq_n_f32 ARM intrinsic
- vmlaq_n_s16 ARM intrinsic
- vmlaq_n_s32 ARM intrinsic
- vmlaq_n_u16 ARM intrinsic
- vmlaq_n_u32 ARM intrinsic
- vmlaq_s16 ARM intrinsic
- vmlaq_s32 ARM intrinsic
- vmlaq_s8 ARM intrinsic
- vmlaq_u16 ARM intrinsic
- vmlaq_u32 ARM intrinsic
- vmlaq_u8 ARM intrinsic
- vmls_f32 ARM intrinsic
- vmls_lane_f32 ARM intrinsic
- vmls_lane_s16 ARM intrinsic
- vmls_lane_s32 ARM intrinsic
- vmls_lane_u16 ARM intrinsic
- vmls_lane_u32 ARM intrinsic
- vmls_n_f32 ARM intrinsic
- vmls_n_s16 ARM intrinsic
- vmls_n_s32 ARM intrinsic
- vmls_n_u16 ARM intrinsic
- vmls_n_u32 ARM intrinsic
- vmls_s16 ARM intrinsic
- vmls_s32 ARM intrinsic
- vmls_s8 ARM intrinsic
- vmls_u16 ARM intrinsic
- vmls_u32 ARM intrinsic
- vmls_u8 ARM intrinsic
- vmlsl_lane_s16 ARM intrinsic
- vmlsl_lane_s32 ARM intrinsic
- vmlsl_lane_u16 ARM intrinsic
- vmlsl_lane_u32 ARM intrinsic
- vmlsl_n_s16 ARM intrinsic
- vmlsl_n_s32 ARM intrinsic
- vmlsl_n_u16 ARM intrinsic
- vmlsl_n_u32 ARM intrinsic
- vmlsl_s16 ARM intrinsic
- vmlsl_s32 ARM intrinsic
- vmlsl_s8 ARM intrinsic
- vmlsl_u16 ARM intrinsic
- vmlsl_u32 ARM intrinsic
- vmlsl_u8 ARM intrinsic
- vmlsq_lane_f32 ARM intrinsic
- vmlsq_lane_s16 ARM intrinsic
- vmlsq_lane_s32 ARM intrinsic
- vmlsq_lane_u16 ARM intrinsic
- vmlsq_lane_u32 ARM intrinsic
- vmlsq_n_f32 ARM intrinsic
- vmlsq_n_s16 ARM intrinsic
- vmlsq_n_s32 ARM intrinsic
- vmlsq_n_u16 ARM intrinsic
- vmlsq_n_u32 ARM intrinsic
- vmlsq_s16 ARM intrinsic
- vmlsq_s32 ARM intrinsic
- vmlsq_s8 ARM intrinsic
- vmov_n_f32 ARM intrinsic
- vmov_n_p16 ARM intrinsic
- vmov_n_p8 ARM intrinsic
- vmov_n_s16 ARM intrinsic
- vmov_n_s32 ARM intrinsic
- vmov_n_s64 ARM intrinsic
- vmov_n_s8 ARM intrinsic
- vmov_n_u16 ARM intrinsic
- vmov_n_u32 ARM intrinsic
- vmov_n_u64 ARM intrinsic
- vmov_n_u8 ARM intrinsic
- vmovl_s16 ARM intrinsic
- vmovl_s32 ARM intrinsic
- vmovl_s8 ARM intrinsic
- vmovl_u16 ARM intrinsic
- vmovl_u32 ARM intrinsic
- vmovl_u8 ARM intrinsic
- vmovn_s16 ARM intrinsic
- vmovn_s32 ARM intrinsic
- vmovn_s64 ARM intrinsic
- vmovn_u16 ARM intrinsic
- vmovn_u32 ARM intrinsic
- vmovn_u64 ARM intrinsic
- vmovq_n_f32 ARM intrinsic
- vmovq_n_p16 ARM intrinsic
- vmovq_n_p8 ARM intrinsic
- vmovq_n_s16 ARM intrinsic
- vmovq_n_s32 ARM intrinsic
- vmovq_n_s64 ARM intrinsic
- vmovq_n_s8 ARM intrinsic
- vmovq_n_u16 ARM intrinsic
- vmovq_n_u32 ARM intrinsic
- vmovq_n_u64 ARM intrinsic
- vmovq_n_u8 ARM intrinsic
- vmul_f32 ARM intrinsic
- vmul_n_f32 ARM intrinsic
- vmul_n_s16 ARM intrinsic
- vmul_n_s32 ARM intrinsic
- vmul_n_u16 ARM intrinsic
- vmul_n_u32 ARM intrinsic
- vmul_p8 ARM intrinsic
- vmul_s16 ARM intrinsic
- vmul_s32 ARM intrinsic
- vmul_s8 ARM intrinsic
- vmul_u16 ARM intrinsic
- vmul_u32 ARM intrinsic
- vmul_u8 ARM intrinsic
- vmull_lane_s16 ARM intrinsic
- vmull_lane_s32 ARM intrinsic
- vmull_lane_u16 ARM intrinsic
- vmull_lane_u32 ARM intrinsic
- vmull_n_s16 ARM intrinsic
- vmull_n_s32 ARM intrinsic
- vmull_n_u16 ARM intrinsic
- vmull_n_u32 ARM intrinsic
- vmull_p8 ARM intrinsic
- vmull_s16 ARM intrinsic
- vmull_s32 ARM intrinsic
- vmull_s8 ARM intrinsic
- vmull_u16 ARM intrinsic
- vmull_u32 ARM intrinsic
- vmull_u8 ARM intrinsic
- vmulq_f32 ARM intrinsic
- vmulq_n_f32 ARM intrinsic
- vmulq_n_s16 ARM intrinsic
- vmulq_n_s32 ARM intrinsic
- vmulq_n_u16 ARM intrinsic
- vmulq_n_u32 ARM intrinsic
- vmulq_p8 ARM intrinsic
- vmulq_s16 ARM intrinsic
- vmulq_s32 ARM intrinsic
- vmulq_s8 ARM intrinsic
- vmulq_u16 ARM intrinsic
- vmulq_u32 ARM intrinsic
- vmulq_u8 ARM intrinsic
- vmvn_p8 ARM intrinsic
- vmvn_s16 ARM intrinsic
- vmvn_s32 ARM intrinsic
- vmvn_s8 ARM intrinsic
- vmvn_u16 ARM intrinsic
- vmvn_u32 ARM intrinsic
- vmvn_u8 ARM intrinsic
- vmvnq_p8 ARM intrinsic
- vmvnq_s16 ARM intrinsic
- vmvnq_s32 ARM intrinsic
- vmvnq_s8 ARM intrinsic
- vmvnq_u16 ARM intrinsic
- vmvnq_u32 ARM intrinsic
- vmvnq_u8 ARM intrinsic
- vneg_f32 ARM intrinsic
- vneg_s16 ARM intrinsic
- vneg_s32 ARM intrinsic
- vneg_s8 ARM intrinsic
- vnegq_f32 ARM intrinsic
- vnegq_s16 ARM intrinsic
- vnegq_s32 ARM intrinsic
- vnegq_s8 ARM intrinsic
- vorn_s16 ARM intrinsic
- vorn_s32 ARM intrinsic
- vorn_s64 ARM intrinsic
- vorn_s8 ARM intrinsic
- vorn_u16 ARM intrinsic
- vorn_u32 ARM intrinsic
- vorn_u64 ARM intrinsic
- vorn_u8 ARM intrinsic
- vornq_s16 ARM intrinsic
- vornq_s32 ARM intrinsic
- vornq_s64 ARM intrinsic
- vornq_s8 ARM intrinsic
- vornq_u16 ARM intrinsic
- vornq_u32 ARM intrinsic
- vornq_u64 ARM intrinsic
- vornq_u8 ARM intrinsic
- vorr_s16 ARM intrinsic
- vorr_s32 ARM intrinsic
- vorr_s64 ARM intrinsic
- vorr_s8 ARM intrinsic
- vorr_u16 ARM intrinsic
- vorr_u32 ARM intrinsic
- vorr_u64 ARM intrinsic
- vorr_u8 ARM intrinsic
- vorrq_s16 ARM intrinsic
- vorrq_s32 ARM intrinsic
- vorrq_s64 ARM intrinsic
- vorrq_s8 ARM intrinsic
- vorrq_u16 ARM intrinsic
- vorrq_u32 ARM intrinsic
- vorrq_u64 ARM intrinsic
- vorrq_u8 ARM intrinsic
- vpadal_s16 ARM intrinsic
- vpadal_s32 ARM intrinsic
- vpadal_s8 ARM intrinsic
- vpadal_u16 ARM intrinsic
- vpadal_u32 ARM intrinsic
- vpadal_u8 ARM intrinsic
- vpadalq_s16 ARM intrinsic
- vpadalq_s32 ARM intrinsic
- vpadalq_s8 ARM intrinsic
- vpadalq_u16 ARM intrinsic
- vpadalq_u32 ARM intrinsic
- vpadalq_u8 ARM intrinsic
- vpadd_f32 ARM intrinsic
- vpadd_s16 ARM intrinsic
- vpadd_s32 ARM intrinsic
- vpadd_s8 ARM intrinsic
- vpadd_u16 ARM intrinsic
- vpadd_u32 ARM intrinsic
- vpadd_u8 ARM intrinsic
- vpaddl_s16 ARM intrinsic
- vpaddl_s32 ARM intrinsic
- vpaddl_s8 ARM intrinsic
- vpaddl_u16 ARM intrinsic
- vpaddl_u32 ARM intrinsic
- vpaddl_u8 ARM intrinsic
- vpaddlq_s16 ARM intrinsic
- vpaddlq_s32 ARM intrinsic
- vpaddlq_s8 ARM intrinsic
- vpaddlq_u16 ARM intrinsic
- vpaddlq_u32 ARM intrinsic
- vpaddlq_u8 ARM intrinsic
- vpmax_f32 ARM intrinsic
- vpmax_s16 ARM intrinsic
- vpmax_s32 ARM intrinsic
- vpmax_s8 ARM intrinsic
- vpmax_u16 ARM intrinsic
- vpmax_u32 ARM intrinsic
- vpmax_u8 ARM intrinsic
- vpmin_f32 ARM intrinsic
- vpmin_s16 ARM intrinsic
- vpmin_s32 ARM intrinsic
- vpmin_s8 ARM intrinsic
- vpmin_u16 ARM intrinsic
- vpmin_u32 ARM intrinsic
- vpmin_u8 ARM intrinsic
- vqabs_s16 ARM intrinsic
- vqabs_s32 ARM intrinsic
- vqabs_s8 ARM intrinsic
- vqabsq_s16 ARM intrinsic
- vqabsq_s32 ARM intrinsic
- vqabsq_s8 ARM intrinsic
- vqadd_s16 ARM intrinsic
- vqadd_s32 ARM intrinsic
- vqadd_s64 ARM intrinsic
- vqadd_s8 ARM intrinsic
- vqadd_u16 ARM intrinsic
- vqadd_u32 ARM intrinsic
- vqadd_u64 ARM intrinsic
- vqadd_u8 ARM intrinsic
- vqaddq_s16 ARM intrinsic
- vqaddq_s32 ARM intrinsic
- vqaddq_s64 ARM intrinsic
- vqaddq_s8 ARM intrinsic
- vqaddq_u16 ARM intrinsic
- vqaddq_u32 ARM intrinsic
- vqaddq_u64 ARM intrinsic
- vqaddq_u8 ARM intrinsic
- vqdmlal_lane_s16 ARM intrinsic
- vqdmlal_lane_s32 ARM intrinsic
- vqdmlal_n_s16 ARM intrinsic
- vqdmlal_n_s32 ARM intrinsic
- vqdmlal_s16 ARM intrinsic
- vqdmlal_s32 ARM intrinsic
- vqdmlsl_lane_s16 ARM intrinsic
- vqdmlsl_lane_s32 ARM intrinsic
- vqdmlsl_n_s16 ARM intrinsic
- vqdmlsl_n_s32 ARM intrinsic
- vqdmlsl_s16 ARM intrinsic
- vqdmlsl_s32 ARM intrinsic
- vqdmulh_lane_s16 ARM intrinsic
- vqdmulh_lane_s32 ARM intrinsic
- vqdmulh_n_s16 ARM intrinsic
- vqdmulh_n_s32 ARM intrinsic
- vqdmulh_s16 ARM intrinsic
- vqdmulh_s32 ARM intrinsic
- vqdmulhq_lane_s16 ARM intrinsic
- vqdmulhq_lane_s32 ARM intrinsic
- vqdmulhq_n_s16 ARM intrinsic
- vqdmulhq_n_s32 ARM intrinsic
- vqdmulhq_s16 ARM intrinsic
- vqdmulhq_s32 ARM intrinsic
- vqdmull_lane_s16 ARM intrinsic
- vqdmull_lane_s32 ARM intrinsic
- vqdmull_n_s16 ARM intrinsic
- vqdmull_n_s32 ARM intrinsic
- vqdmull_s16 ARM intrinsic
- vqdmull_s32 ARM intrinsic
- vqmovn_s16 ARM intrinsic
- vqmovn_s32 ARM intrinsic
- vqmovn_s64 ARM intrinsic
- vqmovn_u16 ARM intrinsic
- vqmovn_u32 ARM intrinsic
- vqmovn_u64 ARM intrinsic
- vqmovun_s16 ARM intrinsic
- vqmovun_s32 ARM intrinsic
- vqmovun_s64 ARM intrinsic
- vqneg_s16 ARM intrinsic
- vqneg_s32 ARM intrinsic
- vqneg_s8 ARM intrinsic
- vqnegq_s16 ARM intrinsic
- vqnegq_s32 ARM intrinsic
- vqnegq_s8 ARM intrinsic
- vqrdmulh_lane_s16 ARM intrinsic
- vqrdmulh_lane_s32 ARM intrinsic
- vqrdmulh_n_s16 ARM intrinsic
- vqrdmulh_n_s32 ARM intrinsic
- vqrdmulh_s16 ARM intrinsic
- vqrdmulh_s32 ARM intrinsic
- vqrdmulhq_lane_s16 ARM intrinsic
- vqrdmulhq_lane_s32 ARM intrinsic
- vqrdmulhq_n_s16 ARM intrinsic
- vqrdmulhq_n_s32 ARM intrinsic
- vqrdmulhq_s16 ARM intrinsic
- vqrdmulhq_s32 ARM intrinsic
- vqrshl_s16 ARM intrinsic
- vqrshl_s32 ARM intrinsic
- vqrshl_s64 ARM intrinsic
- vqrshl_s8 ARM intrinsic
- vqrshl_u16 ARM intrinsic
- vqrshl_u32 ARM intrinsic
- vqrshl_u64 ARM intrinsic
- vqrshl_u8 ARM intrinsic
- vqrshlq_s16 ARM intrinsic
- vqrshlq_s32 ARM intrinsic
- vqrshlq_s64 ARM intrinsic
- vqrshlq_s8 ARM intrinsic
- vqrshlq_u16 ARM intrinsic
- vqrshlq_u32 ARM intrinsic
- vqrshlq_u64 ARM intrinsic
- vqrshlq_u8 ARM intrinsic
- vqrshrn_n_s16 ARM intrinsic
- vqrshrn_n_s32 ARM intrinsic
- vqrshrn_n_s64 ARM intrinsic
- vqrshrn_n_u16 ARM intrinsic
- vqrshrn_n_u32 ARM intrinsic
- vqrshrn_n_u64 ARM intrinsic
- vqrshrun_n_s16 ARM intrinsic
- vqrshrun_n_s32 ARM intrinsic
- vqrshrun_n_s64 ARM intrinsic
- vqshl_n_s16 ARM intrinsic
- vqshl_n_s32 ARM intrinsic
- vqshl_n_s64 ARM intrinsic
- vqshl_n_s8 ARM intrinsic
- vqshl_n_u16 ARM intrinsic
- vqshl_n_u32 ARM intrinsic
- vqshl_n_u64 ARM intrinsic
- vqshl_n_u8 ARM intrinsic
- vqshl_s16 ARM intrinsic
- vqshl_s32 ARM intrinsic
- vqshl_s64 ARM intrinsic
- vqshl_s8 ARM intrinsic
- vqshl_u16 ARM intrinsic
- vqshl_u32 ARM intrinsic
- vqshl_u64 ARM intrinsic
- vqshl_u8 ARM intrinsic
- vqshlq_n_s16 ARM intrinsic
- vqshlq_n_s32 ARM intrinsic
- vqshlq_n_s64 ARM intrinsic
- vqshlq_n_s8 ARM intrinsic
- vqshlq_n_u16 ARM intrinsic
- vqshlq_n_u32 ARM intrinsic
- vqshlq_n_u64 ARM intrinsic
- vqshlq_n_u8 ARM intrinsic
- vqshlq_s16 ARM intrinsic
- vqshlq_s32 ARM intrinsic
- vqshlq_s64 ARM intrinsic
- vqshlq_s8 ARM intrinsic
- vqshlq_u16 ARM intrinsic
- vqshlq_u32 ARM intrinsic
- vqshlq_u64 ARM intrinsic
- vqshlq_u8 ARM intrinsic
- vqshlu_n_s16 ARM intrinsic
- vqshlu_n_s32 ARM intrinsic
- vqshlu_n_s64 ARM intrinsic
- vqshlu_n_s8 ARM intrinsic
- vqshluq_n_s16 ARM intrinsic
- vqshluq_n_s32 ARM intrinsic
- vqshluq_n_s64 ARM intrinsic
- vqshluq_n_s8 ARM intrinsic
- vqshrn_n_s16 ARM intrinsic
- vqshrn_n_s32 ARM intrinsic
- vqshrn_n_s64 ARM intrinsic
- vqshrn_n_u16 ARM intrinsic
- vqshrn_n_u32 ARM intrinsic
- vqshrn_n_u64 ARM intrinsic
- vqshrun_n_s16 ARM intrinsic
- vqshrun_n_s32 ARM intrinsic
- vqshrun_n_s64 ARM intrinsic
- vqsub_s16 ARM intrinsic
- vqsub_s32 ARM intrinsic
- vqsub_s64 ARM intrinsic
- vqsub_s8 ARM intrinsic
- vqsub_u16 ARM intrinsic
- vqsub_u32 ARM intrinsic
- vqsub_u64 ARM intrinsic
- vqsub_u8 ARM intrinsic
- vqsubq_s16 ARM intrinsic
- vqsubq_s32 ARM intrinsic
- vqsubq_s64 ARM intrinsic
- vqsubq_s8 ARM intrinsic
- vqsubq_u16 ARM intrinsic
- vqsubq_u32 ARM intrinsic
- vqsubq_u64 ARM intrinsic
- vqsubq_u8 ARM intrinsic
- vraddhn_s16 ARM intrinsic
- vraddhn_s32 ARM intrinsic
- vraddhn_s64 ARM intrinsic
- vraddhn_u16 ARM intrinsic
- vraddhn_u32 ARM intrinsic
- vraddhn_u64 ARM intrinsic
- vrecpe_f32 ARM intrinsic
- vrecpe_u32 ARM intrinsic
- vrecpeq_f32 ARM intrinsic
- vrecpeq_u32 ARM intrinsic
- vrecps_f32 ARM intrinsic
- vrecpsq_f32 ARM intrinsic
- vrev16_p8 ARM intrinsic
- vrev16_s8 ARM intrinsic
- vrev16_u8 ARM intrinsic
- vrev16q_p8 ARM intrinsic
- vrev16q_s8 ARM intrinsic
- vrev16q_u8 ARM intrinsic
- vrev32_p8 ARM intrinsic
- vrev32_s16 ARM intrinsic
- vrev32_s8 ARM intrinsic
- vrev32_u16 ARM intrinsic
- vrev32_u8 ARM intrinsic
- vrev32q_p8 ARM intrinsic
- vrev32q_s16 ARM intrinsic
- vrev32q_s8 ARM intrinsic
- vrev32q_u16 ARM intrinsic
- vrev32q_u8 ARM intrinsic
- vrev64_f32 ARM intrinsic
- vrev64_p16 ARM intrinsic
- vrev64_p8 ARM intrinsic
- vrev64_s16 ARM intrinsic
- vrev64_s32 ARM intrinsic
- vrev64_s8 ARM intrinsic
- vrev64_u16 ARM intrinsic
- vrev64_u32 ARM intrinsic
- vrev64_u8 ARM intrinsic
- vrev64q_f32 ARM intrinsic
- vrev64q_p16 ARM intrinsic
- vrev64q_p8 ARM intrinsic
- vrev64q_s16 ARM intrinsic
- vrev64q_s32 ARM intrinsic
- vrev64q_s8 ARM intrinsic
- vrev64q_u16 ARM intrinsic
- vrev64q_u32 ARM intrinsic
- vrev64q_u8 ARM intrinsic
- vrhadd_s16 ARM intrinsic
- vrhadd_s32 ARM intrinsic
- vrhadd_s8 ARM intrinsic
- vrhadd_u16 ARM intrinsic
- vrhadd_u32 ARM intrinsic
- vrhadd_u8 ARM intrinsic
- vrhaddq_s16 ARM intrinsic
- vrhaddq_s32 ARM intrinsic
- vrhaddq_s8 ARM intrinsic
- vrhaddq_u16 ARM intrinsic
- vrhaddq_u32 ARM intrinsic
- vrhaddq_u8 ARM intrinsic
- vrshl_s16 ARM intrinsic
- vrshl_s32 ARM intrinsic
- vrshl_s64 ARM intrinsic
- vrshl_s8 ARM intrinsic
- vrshl_u16 ARM intrinsic
- vrshl_u32 ARM intrinsic
- vrshl_u64 ARM intrinsic
- vrshl_u8 ARM intrinsic
- vrshlq_s16 ARM intrinsic
- vrshlq_s32 ARM intrinsic
- vrshlq_s64 ARM intrinsic
- vrshlq_s8 ARM intrinsic
- vrshlq_u16 ARM intrinsic
- vrshlq_u32 ARM intrinsic
- vrshlq_u64 ARM intrinsic
- vrshlq_u8 ARM intrinsic
- vrshr_n_s16 ARM intrinsic
- vrshr_n_s32 ARM intrinsic
- vrshr_n_s64 ARM intrinsic
- vrshr_n_s8 ARM intrinsic
- vrshr_n_u16 ARM intrinsic
- vrshr_n_u32 ARM intrinsic
- vrshr_n_u64 ARM intrinsic
- vrshr_n_u8 ARM intrinsic
- vrshrn_n_s16 ARM intrinsic
- vrshrn_n_s32 ARM intrinsic
- vrshrn_n_s64 ARM intrinsic
- vrshrn_n_u16 ARM intrinsic
- vrshrn_n_u32 ARM intrinsic
- vrshrn_n_u64 ARM intrinsic
- vrshrq_n_s16 ARM intrinsic
- vrshrq_n_s32 ARM intrinsic
- vrshrq_n_s64 ARM intrinsic
- vrshrq_n_s8 ARM intrinsic
- vrshrq_n_u16 ARM intrinsic
- vrshrq_n_u32 ARM intrinsic
- vrshrq_n_u64 ARM intrinsic
- vrshrq_n_u8 ARM intrinsic
- vrsqrte_f32 ARM intrinsic
- vrsqrte_u32 ARM intrinsic
- vrsqrteq_f32 ARM intrinsic
- vrsqrteq_u32 ARM intrinsic
- vrsqrts_f32 ARM intrinsic
- vrsqrtsq_f32 ARM intrinsic
- vrsra_n_s16 ARM intrinsic
- vrsra_n_s32 ARM intrinsic
- vrsra_n_s64 ARM intrinsic
- vrsra_n_s8 ARM intrinsic
- vrsra_n_u16 ARM intrinsic
- vrsra_n_u32 ARM intrinsic
- vrsra_n_u64 ARM intrinsic
- vrsra_n_u8 ARM intrinsic
- vrsraq_n_s16 ARM intrinsic
- vrsraq_n_s32 ARM intrinsic
- vrsraq_n_s64 ARM intrinsic
- vrsraq_n_s8 ARM intrinsic
- vrsraq_n_u16 ARM intrinsic
- vrsraq_n_u32 ARM intrinsic
- vrsraq_n_u64 ARM intrinsic
- vrsraq_n_u8 ARM intrinsic
- vrsubhn_s16 ARM intrinsic
- vrsubhn_s32 ARM intrinsic
- vrsubhn_s64 ARM intrinsic
- vrsubhn_u16 ARM intrinsic
- vrsubhn_u32 ARM intrinsic
- vrsubhn_u64 ARM intrinsic
- vset_lane_f32 ARM intrinsic
- vset_lane_p16 ARM intrinsic
- vset_lane_p8 ARM intrinsic
- vset_lane_s16 ARM intrinsic
- vset_lane_s32 ARM intrinsic
- vset_lane_s64 ARM intrinsic
- vset_lane_s8 ARM intrinsic
- vset_lane_u16 ARM intrinsic
- vset_lane_u32 ARM intrinsic
- vset_lane_u64 ARM intrinsic
- vset_lane_u8 ARM intrinsic
- vsetq_lane_f32 ARM intrinsic
- vsetq_lane_p16 ARM intrinsic
- vsetq_lane_p8 ARM intrinsic
- vsetq_lane_s16 ARM intrinsic
- vsetq_lane_s32 ARM intrinsic
- vsetq_lane_s64 ARM intrinsic
- vsetq_lane_s8 ARM intrinsic
- vsetq_lane_u16 ARM intrinsic
- vsetq_lane_u32 ARM intrinsic
- vsetq_lane_u64 ARM intrinsic
- vsetq_lane_u8 ARM intrinsic
- vshl_n_s16 ARM intrinsic
- vshl_n_s32 ARM intrinsic
- vshl_n_s64 ARM intrinsic
- vshl_n_s8 ARM intrinsic
- vshl_n_u16 ARM intrinsic
- vshl_n_u32 ARM intrinsic
- vshl_n_u64 ARM intrinsic
- vshl_n_u8 ARM intrinsic
- vshl_s16 ARM intrinsic
- vshl_s32 ARM intrinsic
- vshl_s64 ARM intrinsic
- vshl_s8 ARM intrinsic
- vshl_u16 ARM intrinsic
- vshl_u32 ARM intrinsic
- vshl_u64 ARM intrinsic
- vshl_u8 ARM intrinsic
- vshll_n_s16 ARM intrinsic
- vshll_n_s32 ARM intrinsic
- vshll_n_s8 ARM intrinsic
- vshll_n_u16 ARM intrinsic
- vshll_n_u32 ARM intrinsic
- vshll_n_u8 ARM intrinsic
- vshlq_n_s16 ARM intrinsic
- vshlq_n_s32 ARM intrinsic
- vshlq_n_s64 ARM intrinsic
- vshlq_n_s8 ARM intrinsic
- vshlq_n_u16 ARM intrinsic
- vshlq_n_u32 ARM intrinsic
- vshlq_n_u64 ARM intrinsic
- vshlq_n_u8 ARM intrinsic
- vshlq_s16 ARM intrinsic
- vshlq_s32 ARM intrinsic
- vshlq_s64 ARM intrinsic
- vshlq_s8 ARM intrinsic
- vshlq_u16 ARM intrinsic
- vshlq_u32 ARM intrinsic
- vshlq_u64 ARM intrinsic
- vshlq_u8 ARM intrinsic
- vshr_n_s16 ARM intrinsic
- vshr_n_s32 ARM intrinsic
- vshr_n_s64 ARM intrinsic
- vshr_n_s8 ARM intrinsic
- vshr_n_u16 ARM intrinsic
- vshr_n_u32 ARM intrinsic
- vshr_n_u64 ARM intrinsic
- vshr_n_u8 ARM intrinsic
- vshrn_n_s16 ARM intrinsic
- vshrn_n_s32 ARM intrinsic
- vshrn_n_s64 ARM intrinsic
- vshrn_n_u16 ARM intrinsic
- vshrn_n_u32 ARM intrinsic
- vshrn_n_u64 ARM intrinsic
- vshrq_n_s16 ARM intrinsic
- vshrq_n_s32 ARM intrinsic
- vshrq_n_s64 ARM intrinsic
- vshrq_n_s8 ARM intrinsic
- vshrq_n_u16 ARM intrinsic
- vshrq_n_u32 ARM intrinsic
- vshrq_n_u64 ARM intrinsic
- vshrq_n_u8 ARM intrinsic
- vsli_n_p16 ARM intrinsic
- vsli_n_p8 ARM intrinsic
- vsli_n_s16 ARM intrinsic
- vsli_n_s32 ARM intrinsic
- vsli_n_s64 ARM intrinsic
- vsli_n_s8 ARM intrinsic
- vsli_n_u16 ARM intrinsic
- vsli_n_u32 ARM intrinsic
- vsli_n_u64 ARM intrinsic
- vsli_n_u8 ARM intrinsic
- vsliq_n_p16 ARM intrinsic
- vsliq_n_p8 ARM intrinsic
- vsliq_n_s16 ARM intrinsic
- vsliq_n_s32 ARM intrinsic
- vsliq_n_s64 ARM intrinsic
- vsliq_n_s8 ARM intrinsic
- vsliq_n_u16 ARM intrinsic
- vsliq_n_u32 ARM intrinsic
- vsliq_n_u64 ARM intrinsic
- vsliq_n_u8 ARM intrinsic
- vsra_n_s16 ARM intrinsic
- vsra_n_s32 ARM intrinsic
- vsra_n_s64 ARM intrinsic
- vsra_n_s8 ARM intrinsic
- vsra_n_u16 ARM intrinsic
- vsra_n_u32 ARM intrinsic
- vsra_n_u64 ARM intrinsic
- vsra_n_u8 ARM intrinsic
- vsraq_n_s16 ARM intrinsic
- vsraq_n_s32 ARM intrinsic
- vsraq_n_s64 ARM intrinsic
- vsraq_n_s8 ARM intrinsic
- vsraq_n_u16 ARM intrinsic
- vsraq_n_u32 ARM intrinsic
- vsraq_n_u64 ARM intrinsic
- vsraq_n_u8 ARM intrinsic
- vsri_n_p16 ARM intrinsic
- vsri_n_p8 ARM intrinsic
- vsri_n_s16 ARM intrinsic
- vsri_n_s32 ARM intrinsic
- vsri_n_s64 ARM intrinsic
- vsri_n_s8 ARM intrinsic
- vsri_n_u16 ARM intrinsic
- vsri_n_u32 ARM intrinsic
- vsri_n_u64 ARM intrinsic
- vsri_n_u8 ARM intrinsic
- vsriq_n_p16 ARM intrinsic
- vsriq_n_p8 ARM intrinsic
- vsriq_n_s16 ARM intrinsic
- vsriq_n_s32 ARM intrinsic
- vsriq_n_s64 ARM intrinsic
- vsriq_n_s8 ARM intrinsic
- vsriq_n_u16 ARM intrinsic
- vsriq_n_u32 ARM intrinsic
- vsriq_n_u64 ARM intrinsic
- vsriq_n_u8 ARM intrinsic
- vst1_f16 ARM intrinsic
- vst1_f32 ARM intrinsic
- vst1_lane_f16 ARM intrinsic
- vst1_lane_f32 ARM intrinsic
- vst1_lane_p16 ARM intrinsic
- vst1_lane_p8 ARM intrinsic
- vst1_lane_s16 ARM intrinsic
- vst1_lane_s32 ARM intrinsic
- vst1_lane_s64 ARM intrinsic
- vst1_lane_s8 ARM intrinsic
- vst1_lane_u16 ARM intrinsic
- vst1_lane_u32 ARM intrinsic
- vst1_lane_u64 ARM intrinsic
- vst1_lane_u8 ARM intrinsic
- vst1_p16 ARM intrinsic
- vst1_p8 ARM intrinsic
- vst1_s16 ARM intrinsic
- vst1_s32 ARM intrinsic
- vst1_s64 ARM intrinsic
- vst1_s8 ARM intrinsic
- vst1_u16 ARM intrinsic
- vst1_u32 ARM intrinsic
- vst1_u64 ARM intrinsic
- vst1_u8 ARM intrinsic
- vst1q_f16 ARM intrinsic
- vst1q_f32 ARM intrinsic
- vst1q_lane_f16 ARM intrinsic
- vst1q_lane_f32 ARM intrinsic
- vst1q_lane_p16 ARM intrinsic
- vst1q_lane_p8 ARM intrinsic
- vst1q_lane_s16 ARM intrinsic
- vst1q_lane_s32 ARM intrinsic
- vst1q_lane_s64 ARM intrinsic
- vst1q_lane_s8 ARM intrinsic
- vst1q_lane_u16 ARM intrinsic
- vst1q_lane_u32 ARM intrinsic
- vst1q_lane_u64 ARM intrinsic
- vst1q_lane_u8 ARM intrinsic
- vst1q_p16 ARM intrinsic
- vst1q_p8 ARM intrinsic
- vst1q_s16 ARM intrinsic
- vst1q_s32 ARM intrinsic
- vst1q_s64 ARM intrinsic
- vst1q_s8 ARM intrinsic
- vst1q_u16 ARM intrinsic
- vst1q_u32 ARM intrinsic
- vst1q_u64 ARM intrinsic
- vst1q_u8 ARM intrinsic
- vst2_f16 ARM intrinsic
- vst2_f32 ARM intrinsic
- vst2_lane_f16 ARM intrinsic
- vst2_lane_f32 ARM intrinsic
- vst2_lane_p16 ARM intrinsic
- vst2_lane_p8 ARM intrinsic
- vst2_lane_s16 ARM intrinsic
- vst2_lane_s32 ARM intrinsic
- vst2_lane_s8 ARM intrinsic
- vst2_lane_u16 ARM intrinsic
- vst2_lane_u32 ARM intrinsic
- vst2_lane_u8 ARM intrinsic
- vst2_p16 ARM intrinsic
- vst2_p8 ARM intrinsic
- vst2_s16 ARM intrinsic
- vst2_s32 ARM intrinsic
- vst2_s64 ARM intrinsic
- vst2_s8 ARM intrinsic
- vst2_u16 ARM intrinsic
- vst2_u32 ARM intrinsic
- vst2_u64 ARM intrinsic
- vst2_u8 ARM intrinsic
- vst2q_f16 ARM intrinsic
- vst2q_f32 ARM intrinsic
- vst2q_lane_f16 ARM intrinsic
- vst2q_lane_f32 ARM intrinsic
- vst2q_lane_p16 ARM intrinsic
- vst2q_lane_s16 ARM intrinsic
- vst2q_lane_s32 ARM intrinsic
- vst2q_lane_u16 ARM intrinsic
- vst2q_lane_u32 ARM intrinsic
- vst2q_p16 ARM intrinsic
- vst2q_p8 ARM intrinsic
- vst2q_s16 ARM intrinsic
- vst2q_s32 ARM intrinsic
- vst2q_s8 ARM intrinsic
- vst2q_u16 ARM intrinsic
- vst2q_u32 ARM intrinsic
- vst2q_u8 ARM intrinsic
- vst3_f16 ARM intrinsic
- vst3_f32 ARM intrinsic
- vst3_lane_f16 ARM intrinsic
- vst3_lane_f32 ARM intrinsic
- vst3_lane_p16 ARM intrinsic
- vst3_lane_p8 ARM intrinsic
- vst3_lane_s16 ARM intrinsic
- vst3_lane_s32 ARM intrinsic
- vst3_lane_s8 ARM intrinsic
- vst3_lane_u16 ARM intrinsic
- vst3_lane_u32 ARM intrinsic
- vst3_lane_u8 ARM intrinsic
- vst3_p16 ARM intrinsic
- vst3_p8 ARM intrinsic
- vst3_s16 ARM intrinsic
- vst3_s32 ARM intrinsic
- vst3_s64 ARM intrinsic
- vst3_s8 ARM intrinsic
- vst3_u16 ARM intrinsic
- vst3_u32 ARM intrinsic
- vst3_u64 ARM intrinsic
- vst3_u8 ARM intrinsic
- vst3q_f16 ARM intrinsic
- vst3q_f32 ARM intrinsic
- vst3q_lane_f16 ARM intrinsic
- vst3q_lane_f32 ARM intrinsic
- vst3q_lane_p16 ARM intrinsic
- vst3q_lane_s16 ARM intrinsic
- vst3q_lane_s32 ARM intrinsic
- vst3q_lane_u16 ARM intrinsic
- vst3q_lane_u32 ARM intrinsic
- vst3q_p16 ARM intrinsic
- vst3q_p8 ARM intrinsic
- vst3q_s16 ARM intrinsic
- vst3q_s32 ARM intrinsic
- vst3q_s8 ARM intrinsic
- vst3q_u16 ARM intrinsic
- vst3q_u32 ARM intrinsic
- vst3q_u8 ARM intrinsic
- vst4_f16 ARM intrinsic
- vst4_f32 ARM intrinsic
- vst4_lane_f16 ARM intrinsic
- vst4_lane_f32 ARM intrinsic
- vst4_lane_p16 ARM intrinsic
- vst4_lane_p8 ARM intrinsic
- vst4_lane_s16 ARM intrinsic
- vst4_lane_s32 ARM intrinsic
- vst4_lane_s8 ARM intrinsic
- vst4_lane_u16 ARM intrinsic
- vst4_lane_u32 ARM intrinsic
- vst4_lane_u8 ARM intrinsic
- vst4_p16 ARM intrinsic
- vst4_p8 ARM intrinsic
- vst4_s16 ARM intrinsic
- vst4_s32 ARM intrinsic
- vst4_s64 ARM intrinsic
- vst4_s8 ARM intrinsic
- vst4_u16 ARM intrinsic
- vst4_u32 ARM intrinsic
- vst4_u64 ARM intrinsic
- vst4_u8 ARM intrinsic
- vst4q_f16 ARM intrinsic
- vst4q_f32 ARM intrinsic
- vst4q_lane_f16 ARM intrinsic
- vst4q_lane_f32 ARM intrinsic
- vst4q_lane_p16 ARM intrinsic
- vst4q_lane_s16 ARM intrinsic
- vst4q_lane_s32 ARM intrinsic
- vst4q_lane_u16 ARM intrinsic
- vst4q_lane_u32 ARM intrinsic
- vst4q_p16 ARM intrinsic
- vst4q_p8 ARM intrinsic
- vst4q_s16 ARM intrinsic
- vst4q_s32 ARM intrinsic
- vst4q_s8 ARM intrinsic
- vst4q_u16 ARM intrinsic
- vst4q_u32 ARM intrinsic
- vst4q_u8 ARM intrinsic
- vsub_f32 ARM intrinsic
- vsub_s16 ARM intrinsic
- vsub_s32 ARM intrinsic
- vsub_s64 ARM intrinsic
- vsub_s8 ARM intrinsic
- vsub_u16 ARM intrinsic
- vsub_u32 ARM intrinsic
- vsub_u64 ARM intrinsic
- vsub_u8 ARM intrinsic
- vsubhn_s16 ARM intrinsic
- vsubhn_s32 ARM intrinsic
- vsubhn_s64 ARM intrinsic
- vsubhn_u16 ARM intrinsic
- vsubhn_u32 ARM intrinsic
- vsubhn_u64 ARM intrinsic
- vsubl_s16 ARM intrinsic
- vsubl_s32 ARM intrinsic
- vsubl_s8 ARM intrinsic
- vsubl_u16 ARM intrinsic
- vsubl_u32 ARM intrinsic
- vsubl_u8 ARM intrinsic
- vsubq_f32 ARM intrinsic
- vsubq_s16 ARM intrinsic
- vsubq_s32 ARM intrinsic
- vsubq_s64 ARM intrinsic
- vsubq_s8 ARM intrinsic
- vsubq_u16 ARM intrinsic
- vsubq_u32 ARM intrinsic
- vsubq_u64 ARM intrinsic
- vsubq_u8 ARM intrinsic
- vsubw_s16 ARM intrinsic
- vsubw_s32 ARM intrinsic
- vsubw_s8 ARM intrinsic
- vsubw_u16 ARM intrinsic
- vsubw_u32 ARM intrinsic
- vsubw_u8 ARM intrinsic
- vtbl1_p8 ARM intrinsic
- vtbl1_s8 ARM intrinsic
- vtbl1_u8 ARM intrinsic
- vtbl2_p8 ARM intrinsic
- vtbl2_s8 ARM intrinsic
- vtbl2_u8 ARM intrinsic
- vtbl3_p8 ARM intrinsic
- vtbl3_s8 ARM intrinsic
- vtbl3_u8 ARM intrinsic
- vtbl4_p8 ARM intrinsic
- vtbl4_s8 ARM intrinsic
- vtbl4_u8 ARM intrinsic
- vtbx1_p8 ARM intrinsic
- vtbx1_s8 ARM intrinsic
- vtbx1_u8 ARM intrinsic
- vtbx2_p8 ARM intrinsic
- vtbx2_s8 ARM intrinsic
- vtbx2_u8 ARM intrinsic
- vtbx3_p8 ARM intrinsic
- vtbx3_s8 ARM intrinsic
- vtbx3_u8 ARM intrinsic
- vtbx4_p8 ARM intrinsic
- vtbx4_s8 ARM intrinsic
- vtbx4_u8 ARM intrinsic
- vtrn_f32 ARM intrinsic
- vtrn_p16 ARM intrinsic
- vtrn_p8 ARM intrinsic
- vtrn_s16 ARM intrinsic
- vtrn_s32 ARM intrinsic
- vtrn_s8 ARM intrinsic
- vtrn_u16 ARM intrinsic
- vtrn_u32 ARM intrinsic
- vtrn_u8 ARM intrinsic
- vtrnq_f32 ARM intrinsic
- vtrnq_p16 ARM intrinsic
- vtrnq_p8 ARM intrinsic
- vtrnq_s16 ARM intrinsic
- vtrnq_s32 ARM intrinsic
- vtrnq_s8 ARM intrinsic
- vtrnq_u16 ARM intrinsic
- vtrnq_u32 ARM intrinsic
- vtrnq_u8 ARM intrinsic
- vtst_p8 ARM intrinsic
- vtst_s16 ARM intrinsic
- vtst_s32 ARM intrinsic
- vtst_s8 ARM intrinsic
- vtst_u16 ARM intrinsic
- vtst_u32 ARM intrinsic
- vtst_u8 ARM intrinsic
- vtstq_p8 ARM intrinsic
- vtstq_s16 ARM intrinsic
- vtstq_s32 ARM intrinsic
- vtstq_s8 ARM intrinsic
- vtstq_u16 ARM intrinsic
- vtstq_u32 ARM intrinsic
- vtstq_u8 ARM intrinsic
- vuzp_f32 ARM intrinsic
- vuzp_p16 ARM intrinsic
- vuzp_p8 ARM intrinsic
- vuzp_s16 ARM intrinsic
- vuzp_s32 ARM intrinsic
- vuzp_s8 ARM intrinsic
- vuzp_u16 ARM intrinsic
- vuzp_u32 ARM intrinsic
- vuzp_u8 ARM intrinsic
- vuzpq_f32 ARM intrinsic
- vuzpq_p16 ARM intrinsic
- vuzpq_p8 ARM intrinsic
- vuzpq_s16 ARM intrinsic
- vuzpq_s32 ARM intrinsic
- vuzpq_s8 ARM intrinsic
- vuzpq_u16 ARM intrinsic
- vuzpq_u32 ARM intrinsic
- vuzpq_u8 ARM intrinsic
- vzip_f32 ARM intrinsic
- vzip_p16 ARM intrinsic
- vzip_p8 ARM intrinsic
- vzip_s16 ARM intrinsic
- vzip_s8 ARM intrinsic
- vzip_u16 ARM intrinsic
- vzip_u8 ARM intrinsic
- vzipq_f32 ARM intrinsic
- vzipq_p16 ARM intrinsic
- vzipq_p8 ARM intrinsic
- vzipq_s16 ARM intrinsic
- vzipq_s32 ARM intrinsic
- vzipq_s8 ARM intrinsic
- vzipq_u16 ARM intrinsic
- vzipq_u32 ARM intrinsic
- vzipq_u8 ARM intrinsic
ms.assetid: d3d7dadd-7bd5-4508-8bff-371a66913e20
ms.openlocfilehash: 0b0ad779ad9d4c8de1623ea84dd6bc54e30703cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754491"
---
# <a name="arm-intrinsics"></a>ARM – vnitřní funkce

Kompilátor Microsoft C++ (MSVC) zpřístupňuje následující vnitřní objekty na architektuře ARM. Další informace o ARM naleznete v části Nástroje pro architekturu a vývoj softwaru na webu [dokumentace pro vývojáře ARM.](https://developer.arm.com/docs)

## <a name="neon"></a><a name="top"></a>Neon

Neon vektorové instrukční sady rozšíření pro ARM poskytují jeden instrukce více dat (SIMD) schopnosti, které se podobají ty v MMX a SSE vektorové instrukční sady, které jsou společné pro x86 a x64 architektura procesory.

Neon vnitřní jsou podporovány, jak je uvedeno `arm_neon.h`v záhlaví souboru . Podpora MSVC pro VLASTNÍ objekty NEON se podobá kompilátoru ARM, který je popsán v dodatku G [řetězce nástrojů kompilátoru ARM verze 4.1 na](https://go.microsoft.com/fwlink/p/?LinkId=251083) webu INFOCentra ARM.

Hlavní rozdíl mezi MSVC a ARM kompilátor je, `_ex` že MSVC přidává varianty `vldX` a `vstX` vektorové zatížení a ukládání pokynů. Varianty `_ex` trvat další parametr, který určuje zarovnání argumentu ukazatele,`_ex` ale jsou jinak identické s jejich protějšky.

## <a name="arm-specific-intrinsics-listing"></a><a name="A"></a>Arm-specifické vnitřní seznam

|Název funkce|Instrukce|Prototyp funkce|
|-------------------|-----------------|------------------------|
|_arm_smlal|SMLAL|__int64 _arm_smlal(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_umlal|UMLAL|nepodepsané __int64 _arm_umlal \_(nepodepsané _int64 _RdHiLo, nepodepsané int _Rn, nepodepsané int _Rm)|
|_arm_clz|CLZ|nepodepsaný int _arm_clz (nepodepsaný int _Rm)|
|_arm_qadd|QADD|int _arm_qadd (int _Rm, int _Rn)|
|_arm_qdadd|Funkce QDADD|int _arm_qdadd (int _Rm, int _Rn)|
|_arm_qdsub|Funkce QDSUB|int _arm_qdsub (int _Rm, int _Rn)|
|_arm_qsub|QSUB|int _arm_qsub (int _Rm, int _Rn)|
|_arm_smlabb|SMLABB|int _arm_smlabb (int _Rn, int _Rm, int _Ra)|
|_arm_smlabt|SMLABT|int _arm_smlabt (int _Rn, int _Rm, int _Ra)|
|_arm_smlatb|SMLATB|int _arm_smlatb (int _Rn, int _Rm, int _Ra)|
|_arm_smlatt|SMLATT|int _arm_smlatt (int _Rn, int _Rm, int _Ra)|
|_arm_smlalbb|SMLALBB|__int64 _arm_smlalbb(\__RdHiLo _int64, int _Rn, int _Rm)|
|_arm_smlalbt|SMLALBT|__int64 _arm_smlalbt(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlaltb|SMLALTB|__int64 _arm_smlaltb(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlaltt|SMLALTT|__int64 _arm_smlaltt(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlawb|SMLAWB|int _arm_smlawb (int _Rn, int _Rm, int _Ra)|
|_arm_smlawt|SMLAWT|int _arm_smlawt (int _Rn, int _Rm, int _Ra)|
|_arm_smulbb|SMULBB|int _arm_smulbb (int _Rn, int _Rm)|
|_arm_smulbt|SMULBT|int _arm_smulbt (int _Rn, int _Rm)|
|_arm_smultb|SMULTB|int _arm_smultb (int _Rn, int _Rm)|
|_arm_smultt|SMULTT|int _arm_smultt (int _Rn, int _Rm)|
|_arm_smulwb|SMULWB|int _arm_smulwb (int _Rn, int _Rm)|
|_arm_smulwt|SMULWT|int _arm_smulwt (int _Rn, int _Rm)|
|_arm_sadd16|SADD16|int _arm_sadd16 (int _Rn, int _Rm)|
|_arm_sadd8|SADD8|int _arm_sadd8 (int _Rn, int _Rm)|
|_arm_sasx|SASX|int _arm_sasx (int _Rn, int _Rm)|
|_arm_ssax|SSAX|int _arm_ssax (int _Rn, int _Rm)|
|_arm_ssub16|SSUB16|int _arm_ssub16 (int _Rn, int _Rm)|
|_arm_ssub8|SSUB8|int _arm_ssub8 (int _Rn, int _Rm)|
|_arm_shadd16|SHADD16|int _arm_shadd16 (int _Rn, int _Rm)|
|_arm_shadd8|SHADD8|int _arm_shadd8 (int _Rn, int _Rm)|
|_arm_shasx|SHASX|int _arm_shasx (int _Rn, int _Rm)|
|_arm_shsax|Shsax|int _arm_shsax (int _Rn, int _Rm)|
|_arm_shsub16|SHSUB16 ŘEKL:|int _arm_shsub16 (int _Rn, int _Rm)|
|_arm_shsub8|SHSUB8|int _arm_shsub8 (int _Rn, int _Rm)|
|_arm_qadd16|QADD16|int _arm_qadd16 (int _Rn, int _Rm)|
|_arm_qadd8|QADD8|int _arm_qadd8 (int _Rn, int _Rm)|
|_arm_qasx|QASX|int _arm_qasx (int _Rn, int _Rm)|
|_arm_qsax|QSAX|int _arm_qsax (int _Rn, int _Rm)|
|_arm_qsub16|QSUB16|int _arm_qsub16 (int _Rn, int _Rm)|
|_arm_qsub8|QSUB8|int _arm_qsub8 (int _Rn, int _Rm)|
|_arm_uadd16|UADD16|nepodepsaný int _arm_uadd16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uadd8|UADD8|nepodepsaný int _arm_uadd8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uasx|UASX|nepodepsaný int _arm_uasx (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_usax|USAX|nepodepsaný int _arm_usax (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_usub16|USUB16|nepodepsaný int _arm_usub16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_usub8|USUB8|nepodepsaný int _arm_usub8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhadd16|UHADD16|nepodepsaný int _arm_uhadd16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhadd8|UHADD8|nepodepsaný int _arm_uhadd8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhasx|UHASX|nepodepsaný int _arm_uhasx (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhsax|UHSAX|nepodepsaný int _arm_uhsax (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhsub16|UHSUB16|nepodepsaný int _arm_uhsub16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uhsub8|UHSUB8|nepodepsaný int _arm_uhsub8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqadd16|UQADD16|nepodepsaný int _arm_uqadd16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqadd8|UQADD8|nepodepsaný int _arm_uqadd8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqasx|UQASX|nepodepsaný int _arm_uqasx (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqsax|UQsax|nepodepsaný int _arm_uqsax (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqsub16|UQSUB16|nepodepsaný int _arm_uqsub16 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_uqsub8|UQSUB8|nepodepsaný int _arm_uqsub8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_sxtab|SXTAB|int _arm_sxtab (int _Rn, int _Rm, nepodepsaný int _Rotation)|
|_arm_sxtab16|SXTAB16|int _arm_sxtab16 (int _Rn, int _Rm, nepodepsaný int _Rotation)|
|_arm_sxtah|SXTAH|int _arm_sxtah (int _Rn, int _Rm, nepodepsaný int _Rotation)|
|_arm_uxtab|UXTAB|nepodepsaný int _arm_uxtab (nepodepsaný int _Rn, nepodepsaný int _Rm, nepodepsaný int _Rotation)|
|_arm_uxtab16|UXTAB16|nepodepsaný int _arm_uxta16b (nepodepsaný int _Rn, nepodepsaný int _Rm, nepodepsaný int _Rotation)|
|_arm_uxtah|UXTAH|nepodepsaný int _arm_uxtah (nepodepsaný int _Rn, nepodepsaný int _Rm, nepodepsaný int _Rotation)|
|_arm_sxtb|SXTB|int _arm_sxtb (int _Rn, nepodepsaný int _Rotation)|
|_arm_sxtb16|SXTB16|int _arm_sxtb16 (int _Rn, nepodepsaný int _Rotation)|
|_arm_sxth|SXTH|int _arm_sxth (int _Rn, nepodepsaný int _Rotation)|
|_arm_uxtb|UXTB|nepodepsaný int _arm_uxtb (nepodepsaný int _Rn, nepodepsaný int _Rotation)|
|_arm_uxtb16|UXTB16|nepodepsaný int _arm_uxtb16 (nepodepsaný int _Rn, nepodepsaný int _Rotation)|
|_arm_uxth|UXTH|nepodepsaný int _arm_uxth (nepodepsaný int _Rn, nepodepsaný int _Rotation)|
|_arm_pkhbt|PKHBT|int _arm_pkhbt (int _Rn, int _Rm, nepodepsaný int _Lsl_imm)|
|_arm_pkhtb|PKHTB|int _arm_pkhtb (int _Rn, int _Rm, nepodepsaný int _Asr_imm)|
|_arm_usad8|USAD8|nepodepsaný int _arm_usad8 (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|_arm_usada8|USADA8|nepodepsaný int _arm_usada8 (nepodepsaný int _Rn, nepodepsaný int _Rm, nepodepsaný int _Ra)|
|_arm_ssat|SSAT|int _arm_ssat (nepodepsaný int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, nepodepsaný int _Shift_imm)|
|_arm_usat|USAT|int _arm_usat (nepodepsaný int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, nepodepsaný int _Shift_imm)|
|_arm_ssat16|SSAT16|int _arm_ssat16 (nepodepsaný int _Sat_imm, _int _Rn)|
|_arm_usat16|USAT16|int _arm_usat16 (nepodepsaný int _Sat_imm, _int _Rn)|
|_arm_rev|Rev|nepodepsaný int _arm_rev (nepodepsaný int _Rm)|
|_arm_rev16|Rev16|nepodepsaný int _arm_rev16 (nepodepsaný int _Rm)|
|_arm_revsh|REVSH|nepodepsaný int _arm_revsh (nepodepsaný int _Rm)|
|_arm_smlad|SMLAD|int _arm_smlad (int _Rn, int _Rm, int _Ra)|
|_arm_smladx|SMLADX|int _arm_smladx (int _Rn, int _Rm, int _Ra)|
|_arm_smlsd|SMLSD|int _arm_smlsd (int _Rn, int _Rm, int _Ra)|
|_arm_smlsdx|SMLSDX|int _arm_smlsdx (int _Rn, int _Rm, int _Ra)|
|_arm_smmla|SMMLA|int _arm_smmla (int _Rn, int _Rm, int _Ra)|
|_arm_smmlar|SMMLAR|int _arm_smmlar (int _Rn, int _Rm, int _Ra)|
|_arm_smmls|SMMLS|int _arm_smmls (int _Rn, int _Rm, int _Ra)|
|_arm_smmlsr|SMMLSR|int _arm_smmlsr (int _Rn, int _Rm, int _Ra)|
|_arm_smmul|SMMUL|int _arm_smmul (int _Rn, int _Rm)|
|_arm_smmulr|SMMULR|int _arm_smmulr (int _Rn, int _Rm)|
|_arm_smlald|SMLALD|__int64 _arm_smlald(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlaldx|SMLALDX|__int64 _arm_smlaldx(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlsld|SMLSLD|__int64 _arm_smlsld(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smlsldx|SMLSLDX|__int64 _arm_smlsldx(\__int64 _RdHiLo, int _Rn, int _Rm)|
|_arm_smuad|SMUAD|int _arm_smuad (int _Rn, int _Rm)|
|_arm_smuadx|SMUADX|int _arm_muadxs (int _Rn, int _Rm)|
|_arm_smusd|SMUSD|int _arm_smusd (int _Rn, int _Rm)|
|_arm_smusdx|SMUSDX|int _arm_smusdx (int _Rn, int _Rm)|
|_arm_smull|SMULL|__int64 _arm_smull (int _Rn, int _Rm)|
|_arm_umull|UMULL|nepodepsané __int64 _arm_umull (nepodepsané int _Rn, nepodepsané int _Rm)|
|_arm_umaal|UMAAL|nepodepsané __int64 _arm_umaal (nepodepsané int _RdLo, nepodepsané int _RdHi, nepodepsané int _Rn, nepodepsané int _Rm)|
|_arm_bfc|BFC|nepodepsaný int _arm_bfc (nepodepsaný int _Rd, nepodepsaný int _Lsb, nepodepsaný int _Width)|
|_arm_bfi|Bfi|nepodepsaný int _arm_bfi (nepodepsaný int _Rd, nepodepsaný int _Rn, nepodepsaný int _Lsb, nepodepsaný int _Width)|
|_arm_rbit|RBIT|nepodepsaný int _arm_rbit (nepodepsaný int _Rm)|
|_arm_sbfx|SBFX|int _arm_sbfx (int _Rn, nepodepsaný int _Lsb, nepodepsaný int _Width)|
|_arm_ubfx|UBFX|nepodepsaný int _arm_ubfx (nepodepsaný int _Rn, nepodepsaný int _Lsb, nepodepsaný int _Width)|
|_arm_sdiv|SDIV|int _arm_sdiv (int _Rn, int _Rm)|
|_arm_udiv|UDIV|nepodepsaný int _arm_udiv (nepodepsaný int _Rn, nepodepsaný int _Rm)|
|__cps|Cps|neplatné __cps (nepodepsaný int _Ops, nepodepsaný int _Flags, nepodepsaný int _Mode)|
|__dmb|Dmb|neplatné __dmb (nepodepsaný int `_Type`)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__dsb|Dsb|neplatné __dsb (nepodepsaný int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__isb|Isb|neplatné __isb (nepodepsaný int _Type)<br /><br /> Vloží operaci bariéry paměti do datového proudu instrukcí. Parametr `_Type` určuje druh omezení, které bariéra vynucuje.<br /><br /> Další informace o typech omezení, která lze vynutit, naleznete v [tématu Omezení bariéry paměti](#BarrierRestrictions).|
|__emit||zrušit __emit (nepodepsaný \__int32 opcode)<br /><br /> Vloží zadanou instrukci do datového proudu instrukcí, který je výstup kompilátoru.<br /><br /> Hodnota `opcode` musí být konstantní výraz, který je znám v době kompilace. Velikost slova instrukce je 16 bitů a nejvýznamnější 16 `opcode` bitů jsou ignorovány.<br /><br /> Kompilátor neprovede žádný pokus `opcode` o interpretaci obsahu a nezaručuje procesor nebo stav paměti před spuštěním vložené instrukce.<br /><br /> Kompilátor předpokládá, že stavy procesoru a paměti jsou nezměněny po spuštění vložené instrukce. Proto pokyny, které změnit stav může mít škodlivý dopad na normální kód, který je generován kompilátorem.<br /><br /> Z tohoto důvodu `emit` použijte pouze k vložení pokynů, které ovlivňují stav procesoru, který kompilátor normálně nezpracovává – `declspec(naked)`například stav koprocesoru – nebo k implementaci funkcí, které jsou deklarovány pomocí .|
|__hvc|HVC|nepodepsaný int __hvc (nepodepsaný int, ...)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatilní \__int16 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatilní \__int32 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (konst. volatilní \__int64 \*)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 \_ \*(_int8)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store16||__iso_volatile_store16 (těkavá \__int16 \*, \__int16)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store32||neplatné __iso_volatile_store32 \_ \*(těkavá _int32 , \__int32)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store64||neplatné __iso_volatile_store64 \_ \*(těkavá _int64 , \__int64)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store8||neplatné __iso_volatile_store8 \_ \*(těkavé _int8 , \__int8)<br /><br /> Další informace naleznete [v tématu __iso_volatile_load/store intrinsics](#IsoVolatileLoadStore).|
|__ldrexd|LDREXD|__int64 \__ldrexd (const volatilní \__int64 \*)|
|__prefetch|Pld|neplatné \___cdecl _prefetch \*(const void )<br /><br /> Poskytuje `PLD` nápovědu paměti do systému, že paměť na nebo v blízkosti zadané adresy lze přistupovat brzy. Některé systémy se mohou rozhodnout optimalizovat pro tento vzor přístupu k paměti pro zvýšení výkonu za běhu. Z hlediska jazyka C++ však funkce nemá žádný pozorovatelný účinek a může neprovádět vůbec žádné funkce.|
|__rdpmccntr64||nepodepsané \___int64 _rdpmccntr64(void)|
|__sev|Sev|neplatné __sev(void)|
|__static_assert||void __static_assert (int, \*const char )|
|__swi|Svc|nepodepsaný int __swi (nepodepsaný int, ...)|
|__trap|BKPT|int __trap(int, ...)|
|__wfe|WFE|neplatné __wfe(void)|
|__wfi|WFI|neplatné __wfi(void)|
|_AddSatInt|QADD|int _AddSatInt(int, int)|
|_CopyDoubleFromInt64||dvojité _CopyDoubleFromInt64(\__int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 plováku(\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat (plovák)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble (dvojitá)|
|_CountLeadingOnes||nepodepsaný int _CountLeadingOnes (nepodepsaný dlouhý)|
|_CountLeadingOnes64||nepodepsaný int _CountLeadingOnes64 \_(nepodepsaný _int64)|
|_CountLeadingSigns||nepodepsaný int _CountLeadingSigns(long)|
|_CountLeadingSigns64||nepodepsaný int\__CountLeadingSigns64( _int64)|
|_CountLeadingZeros||nepodepsaný int _CountLeadingZeros (nepodepsaný dlouhý)|
|_CountLeadingZeros64||nepodepsaný int _CountLeadingZeros64 \_(nepodepsaný _int64)|
|_CountOneBits||nepodepsaný int _CountOneBits (nepodepsaný dlouhý)|
|_CountOneBits64||nepodepsaný int _CountOneBits64 \_(nepodepsaný _int64)|
|_DAddSatInt|Funkce QDADD|int _DAddSatInt(int, int)|
|_DSubSatInt|Funkce QDSUB|int _DSubSatInt (int, int)|
|_isunordered||int _isunordered (dvojité, dvojité)|
|_isunorderedf||int _isunorderedf (plovák, plovák)|
|_MoveFromCoprocessor|Mrc|nepodepsaný int _MoveFromCoprocessor (nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveFromCoprocessor, _MoveFromCoprocessor2](#MoveFromCo).|
|_MoveFromCoprocessor2|MRC2|nepodepsaný int _MoveFromCoprocessor2 (nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveFromCoprocessor, _MoveFromCoprocessor2](#MoveFromCo).|
|_MoveFromCoprocessor64|MRRC|nepodepsané __int64 _MoveFromCoprocessor64 (nepodepsaný int, nepodepsaný int, nepodepsaný int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveFromCoprocessor64](#MoveFromCo64).|
|_MoveToCoprocessor|Mcr|void _MoveToCoprocessor (nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveToCoprocessor, _MoveToCoprocessor2](#MoveToCo).|
|_MoveToCoprocessor2|MCR2|neplatné _MoveToCoprocessor2 (nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int, nepodepsaný int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveToCoprocessor, _MoveToCoprocessor2](#MoveToCo).|
|_MoveToCoprocessor64|MCRR ŘEKL:|zrušit _MoveToCoprocessor64 (nepodepsané \__int64, nepodepsané int, nepodepsané int, nepodepsané int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace naleznete [v tématu _MoveToCoprocessor64](#MoveToCo64).|
|_MulHigh||dlouhé _MulHigh (dlouhé, dlouhé)|
|_MulUnsignedHigh||nepodepsané dlouhé _MulUnsignedHigh (nepodepsané dlouhé, nepodepsané dlouhé)|
|_ReadBankedReg|Paní|int _ReadBankedReg (int _Reg)|
|_ReadStatusReg|Paní|int _ReadStatusReg(int)|
|_SubSatInt|QSUB|int _SubSatInt(int, int)|
|_WriteBankedReg|Msr|_WriteBankedReg (int _Value, int _Reg)|
|_WriteStatusReg|Msr|void _WriteStatusReg (int, int, int)|

[Návrat[na vrchol](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Omezení bariéry paměti

Vnitřní funkce `__dmb` (bariéra paměti dat), `__dsb` (bariéra synchronizace dat) a `__isb` (bariéra synchronizace instrukcí) používají následující předdefinované hodnoty k určení omezení bariéry paměti z hlediska domény sdílení a druhu přístupu, které jsou ovlivněny operací.

|Hodnota omezení|Popis|
|-----------------------|-----------------|
|_ARM_BARRIER_SY|Celý systém, čte a píše.|
|_ARM_BARRIER_ST|Plný systém, pouze zápisy.|
|_ARM_BARRIER_ISH|Vnitřní sharable, čte a píše.|
|_ARM_BARRIER_ISHST|Vnitřní sharable, píše pouze.|
|_ARM_BARRIER_NSH|Non-sharable, čte a píše.|
|_ARM_BARRIER_NSHST|Non-sharable, píše pouze.|
|_ARM_BARRIER_OSH|Vnější sharable, čte a píše.|
|_ARM_BARRIER_OSHST|Vnější sharable, píše pouze.|

`__isb` Pro vnitřní, pouze omezení, které je v současné době platí je _ARM_BARRIER_SY; všechny ostatní hodnoty jsou vyhrazeny architekturou.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/skladové objekty

Tyto vnitřní funkce explicitně provádět zatížení a obchody, které nejsou předmětem optimalizace kompilátoru.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Parametry

*Umístění*\
Adresa umístění v paměti pro čtení nebo zápis.

*Hodnotu*\
Hodnota pro zápis do zadaného umístění paměti (pouze vnitřní objekty úložiště).

#### <a name="return-value-load-intrinsics-only"></a>Vrácená hodnota (pouze vnitřní zatížení)

Hodnota umístění paměti, která je `Location`určena .

#### <a name="remarks"></a>Poznámky

Můžete použít `__iso_volatile_load8/16/32/64` a `__iso_volatile_store8/16/32/64` vnitřní objekty explicitně provádět přístupy k paměti, které nejsou předmětem optimalizace kompilátoru. Kompilátor nelze odebrat, syntetizovat nebo změnit relativní pořadí těchto operací, ale negeneruje implicitní hardwarové paměti bariéry. Proto hardware může stále ustále přiobjednání přístupu pozorovatelné paměti přes více vláken. Přesněji řečeno, tyto vnitřní objekty jsou ekvivalentní následující výrazy, jak je kompilován pod **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Všimněte si, že vnitřní trvat těkavé ukazatele pro uložení těkavých proměnných. Neexistuje však žádný požadavek nebo doporučení použít nestálé ukazatele jako argumenty. Sémantiku těchto operací jsou přesně stejné, pokud je použit pravidelný, nevolatilní typ.

Další informace o argumentu příkazového řádku **/volatile:iso** naleznete [v tématu /volatile (volatile Keyword Interpretation).](../build/reference/volatile-volatile-keyword-interpretation.md)

### <a name="_movefromcoprocessor-_movefromcoprocessor2"></a><a name="MoveFromCo"></a>_MoveFromCoprocessor, _MoveFromCoprocessor2

Tyto vnitřní funkce číst data z arm koprocesorů pomocí pokynů pro přenos dat koprocesoru.

```C
int _MoveFromCoprocessor(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);

int _MoveFromCoprocessor2(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);
```

#### <a name="parameters"></a>Parametry

*koproc*\
Číslo koprocesoru v rozsahu 0 až 15.

*opcode1*\
Operační kód specifický pro koprocesor v rozsahu 0 až 7

*Crn*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje první operand instrukce.

*Crm*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje další zdrojový nebo cílový operand.

*opcode2*\
Další operační kód specifický pro koprocesor v rozsahu 0 až 7.

#### <a name="return-value"></a>Návratová hodnota

Hodnota, která je přečtena z koprocesoru.

#### <a name="remarks"></a>Poznámky

Hodnoty všech pěti parametrů vnitřní musí být konstantní výrazy, které jsou známy v době kompilace.

`_MoveFromCoprocessor`používá pokyn MRC; `_MoveFromCoprocessor2` používá MRC2. Parametry odpovídají bitovým polím, která jsou zakódována přímo do slova instrukce. Interpretace parametrů je závislá na koprocesoru. Další informace naleznete v příručce k dotyčnému koprocesoru.

### <a name="_movefromcoprocessor64"></a><a name="MoveFromCo64"></a>_MoveFromCoprocessor64

Čte data z koprocesorů ARM pomocí pokynů pro přenos dat koprocesoru.

```C
unsigned __int64 _MoveFromCoprocessor64(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>Parametry

*koproc*\
Číslo koprocesoru v rozsahu 0 až 15.

*opcode1*\
Operační kód specifický pro koprocesor v rozsahu 0 až 15.

*Crm*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje další zdrojový nebo cílový operand.

#### <a name="return-value"></a>Návratová hodnota

Hodnota, která je přečtena z koprocesoru.

#### <a name="remarks"></a>Poznámky

Hodnoty všech tří parametrů vnitřní musí být konstantní výrazy, které jsou známy v době kompilace.

`_MoveFromCoprocessor64`používá pokyny MRRC. Parametry odpovídají bitovým polím, která jsou zakódována přímo do slova instrukce. Interpretace parametrů je závislá na koprocesoru. Další informace naleznete v příručce k dotyčnému koprocesoru.

### <a name="_movetocoprocessor-_movetocoprocessor2"></a><a name="MoveToCo"></a>_MoveToCoprocessor, _MoveToCoprocessor2

Tyto vnitřní funkce zapisují data do koprocesorů ARM pomocí pokynů pro přenos dat koprocesoru.

```C
void _MoveToCoprocessor(
      unsigned int value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);

void _MoveToCoprocessor2(
      unsigned int value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);
```

#### <a name="parameters"></a>Parametry

*Hodnotu*\
Hodnota, která má být zapsána do koprocesoru.

*koproc*\
Číslo koprocesoru v rozsahu 0 až 15.

*opcode1*\
Operační kód specifický pro koprocesor v rozsahu 0 až 7.

*Crn*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje první operand instrukce.

*Crm*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje další zdrojový nebo cílový operand.

*opcode2*\
Další operační kód specifický pro koprocesor v rozsahu 0 až 7.

#### <a name="return-value"></a>Návratová hodnota

Žádné.

#### <a name="remarks"></a>Poznámky

Hodnoty `coproc`, `opcode1`, `crn` `crm`, a `opcode2` parametry vnitřní musí být konstantní výrazy, které jsou známy v době kompilace.

`_MoveToCoprocessor`používá instrukce MCR; `_MoveToCoprocessor2` používá MCR2. Parametry odpovídají bitovým polím, která jsou zakódována přímo do slova instrukce. Interpretace parametrů je závislá na koprocesoru. Další informace naleznete v příručce k dotyčnému koprocesoru.

### <a name="_movetocoprocessor64"></a><a name="MoveToCo64"></a>_MoveToCoprocessor64

Tyto vnitřní funkce zapisují data do koprocesorů ARM pomocí pokynů pro přenos dat koprocesoru.

```C
void _MoveFromCoprocessor64(
      unsigned __int64 value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>Parametry

*koproc*\
Číslo koprocesoru v rozsahu 0 až 15.

*opcode1*\
Operační kód specifický pro koprocesor v rozsahu 0 až 15.

*Crm*\
Číslo registru koprocesoru v rozsahu 0 až 15, které určuje další zdrojový nebo cílový operand.

#### <a name="return-value"></a>Návratová hodnota

Žádné.

#### <a name="remarks"></a>Poznámky

Hodnoty `coproc`, `opcode1`a `crm` parametry vnitřní musí být konstantní výrazy, které jsou známy v době kompilace.

`_MoveFromCoprocessor64`používá instrukce MCRR. Parametry odpovídají bitovým polím, která jsou zakódována přímo do slova instrukce. Interpretace parametrů je závislá na koprocesoru. Další informace naleznete v příručce k dotyčnému koprocesoru.

## <a name="arm-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM Podpora pro vnitřní objekty z jiných architektur

V následující tabulce jsou uvedeny vnitřní objekty z jiných architektur, které jsou podporovány na platformách ARM. Kde chování vnitřní arm se liší od jeho chování na jiné hardwarové architektury, jsou zaznamenány další podrobnosti.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|__assume|neplatné __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|neplatné \___cdecl _debugbreak(void)|
|__fastfail|__declspec(noreturn) \_void _fastfail (nepodepsaný int)|
|__nop|void __nop(void) **Poznámka:** Na platformách ARM tato funkce generuje instrukci NOP, pokud je implementována v cílové architektuře; v opačném případě je generována alternativní instrukce, která nemění stav programu `MOV r8, r8`nebo procesoru – například . Je funkčně ekvivalentní \__nop vnitřní pro jiné hardwarové architektury. Vzhledem k tomu, že instrukce, která nemá žádný vliv na stav programu nebo procesoru může být ignorována cílovou architekturou jako optimalizace, instrukce nemusí nutně spotřebovávat cykly procesoru. Proto nepoužívejte \__nop vnitřní manipulovat s dobou provádění sekvence kódu, pokud si nejste jisti, jak se bude procesor chovat. Místo toho můžete \_použít _nop vnitřní zarovnat další instrukce na konkrétní 32bitovou adresu hranice.|
|__yield|void __yield(void) **Poznámka:** Na platformách ARM tato funkce generuje yield instrukce, která označuje, že podproces provádí úlohu, která může být dočasně pozastavena z provádění – například spinlock – bez nepříznivě ovlivnit program. Umožňuje procesoru provádět další úlohy během cyklů provádění, které by jinak byly zbytečné.|
|_AddressOfReturnAddress|neplatné \* _AddressOfReturnAddress(void)|
|_BitScanForward|nepodepsané char _BitScanForward (nepodepsané dlouhé \* _Index, nepodepsané dlouhé _Mask)|
|_BitScanReverse|nepodepsané char _BitScanReverse (nepodepsané dlouhé \* _Index, nepodepsané dlouhé _Mask)|
|_bittest|nepodepsané char _bittest (dlouhé const \*, dlouhé)|
|_bittestandcomplement|nepodepsané znakové \*_bittestandcomplement (dlouhé, dlouhé)|
|_bittestandreset|nepodepsané char _bittestandreset \*(dlouhé , dlouhé)|
|_bittestandset|nepodepsané char _bittestandset \*(dlouhé , dlouhé)|
|_byteswap_uint64|nepodepsané \___int64 _cdecl _byteswap_uint64 \_(nepodepsané _int64)|
|_byteswap_ulong|nepodepsané dlouhé __cdecl _byteswap_ulong (nepodepsané dlouhé)|
|_byteswap_ushort|nepodepsané krátké __cdecl _byteswap_ushort (nepodepsané krátké)|
|_disable|void __cdecl _disable(void) **Poznámka:** Na platformách ARM tato funkce generuje instrukci CPSID; je k dispozici pouze jako vnitřní.|
|_enable|void __cdecl _enable(void) **Poznámka:** Na platformách ARM tato funkce generuje instrukce CPSIE; je k dispozici pouze jako vnitřní.|
|_lrotl|nepodepsané dlouhé __cdecl _lrotl (nepodepsané dlouhé, int)|
|_lrotr|nepodepsané dlouhé __cdecl _lrotr (nepodepsané dlouhé, int)|
|_ReadBarrier|neplatné _ReadBarrier(void)|
|_ReadWriteBarrier|neplatné _ReadWriteBarrier(void)|
|_ReturnAddress|neplatné \* _ReturnAddress(void)|
|_rotl|nepodepsaný int __cdecl _rotl (nepodepsaný int _Value, int _Shift)|
|_rotl16|nepodepsané krátké _rotl16 (nepodepsané krátké _Value, nepodepsané char _Shift)|
|_rotl64|nepodepsané \___int64 _cdecl _rotl64 \_(nepodepsané _int64 _Value, int _Shift)|
|_rotl8|nepodepsané char _rotl8 (nepodepsané char _Value, nepodepsané char _Shift)|
|_rotr|nepodepsaný int __cdecl _rotr (nepodepsaný int _Value, int _Shift)|
|_rotr16|nepodepsané krátké _rotr16 (nepodepsané krátké _Value, nepodepsané char _Shift)|
|_rotr64|nepodepsané \___int64 _cdecl _rotr64 \_(nepodepsané _int64 _Value, int _Shift)|
|_rotr8|nepodepsané char _rotr8 (nepodepsané char _Value, nepodepsané char _Shift)|
|_setjmpex|int __cdecl _setjmpex (jmp_buf)|
|_WriteBarrier|neplatné _WriteBarrier(void)|

[Návrat[na vrchol](#top)]

## <a name="interlocked-intrinsics"></a>Propojené vnitřní objekty

Interlocked vnitřní jsou sada vnitřních částí, které se používají k provádění operací atomické čtení,modifikovat a zápis. Některé z nich jsou společné pro všechny platformy. Jsou zde uvedeny samostatně, protože existuje velké množství z nich, ale protože jejich definice jsou většinou nadbytečné, je snazší o nich přemýšlet obecně. Jejich názvy lze použít k odvození přesné chování.

Následující tabulka shrnuje podporu ARM nebitové interlocked vnitřní objekty. Každá buňka v tabulce odpovídá názvu, který je odvozen připojením názvu operace v buňce řádku zcela vlevo a názvu `_Interlocked`typu v buňce sloupce zcela nahoře . Například buňka v průsečíku `Xor` `8` řádku a `_InterlockedXor8` sloupce odpovídá a je plně podporována. Většina podporovaných funkcí nabízí tyto volitelné `_acq` `_rel`přípony: , a `_nf`. `_acq` Přípona označuje sémantické "získat" `_rel` a přípona označuje "uvolnění" sémantické. Přípona `_nf` "bez plotu" je jedinečná pro ARM a je popsána v další části.

||8|16|32|64|P|
|-|-------|--------|--------|--------|-------|
|Přidat|Žádná|Žádná|Do bloku|Do bloku|Žádná|
|And|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|
|Compareexchange|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|
|Snižovat|Žádná|Do bloku|Do bloku|Do bloku|Žádná|
|Výměna|Částečné|Částečné|Částečné|Částečné|Částečné|
|ExchangeAdd|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|
|Přírůstek|Žádná|Do bloku|Do bloku|Do bloku|Žádná|
|Nebo|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|
|Xor|Do bloku|Do bloku|Do bloku|Do bloku|Žádná|

Klíč:

- **Úplné**: podporuje `_acq` `_rel`prosté, `_nf` , a formuláře.

- **Částečné**: podporuje `_acq`prosté, a `_nf` formuláře.

- **Žádné**: Není podporováno.

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf (bez plotu) Přípona

Přípona `_nf` "bez plotu" označuje, že operace se nechová jako jakýkoli druh bariéry paměti, `_acq`na `_rel`rozdíl od ostatních tří forem (prostý, , a ), které se chovají jako nějaký druh bariéry. Jedním z možných použití `_nf` formulářů je udržovat čítač statistiky, který je aktualizován více vlákny současně, ale jehož hodnota není jinak použita při provádění více vláken.

### <a name="list-of-interlocked-intrinsics"></a>Seznam vzájemně propojených vnitřitních položek

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_InterlockedAdd|dlouhý _InterlockedAdd (dlouhá _volatile, \*dlouhá)|
|_InterlockedAdd64|__int64 _InterlockedAdd64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAdd_acq|dlouhé _InterlockedAdd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedAdd_nf|dlouhé _InterlockedAdd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedAdd_rel|dlouhé _InterlockedAdd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd|dlouhé _InterlockedAnd (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd16|krátké _InterlockedAnd16 (krátké těkavé, \*krátké)|
|_InterlockedAnd16_acq|krátké _InterlockedAnd16_acq (krátké těkavé, \*krátké)|
|_InterlockedAnd16_nf|krátké _InterlockedAnd16_nf (krátké těkavé, \*krátké)|
|_InterlockedAnd16_rel|krátké _InterlockedAnd16_rel (krátké těkavé, \*krátké)|
|_InterlockedAnd64|__int64 _InterlockedAnd64(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedAnd8|char _InterlockedAnd8(char \*těkavé , char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char \*těkavé , char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char těkavé \*, char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char \*těkavé , char)|
|_InterlockedAnd_acq|dlouhé _InterlockedAnd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd_nf|dlouhé _InterlockedAnd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedAnd_rel|dlouhé _InterlockedAnd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedCompareExchange|dlouhé __cdecl _InterlockedCompareExchange \*(dlouhé těkavé , dlouhé, dlouhé)|
|_InterlockedCompareExchange16|krátké _InterlockedCompareExchange16 (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_acq|krátké _InterlockedCompareExchange16_acq (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_nf|krátké _InterlockedCompareExchange16_nf (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange16_rel|krátké _InterlockedCompareExchange16_rel (krátké těkavé \*, krátké, krátké)|
|_InterlockedCompareExchange64|__int64\__InterlockedCompareExchange64( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq( \*_int64 \_volatilní \_, _int64, _int64)|
|_InterlockedCompareExchange64_nf|__int64\__InterlockedCompareExchange64_nf( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64\__InterlockedCompareExchange64_rel( \*_int64 \_volatilní, _int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char těkavé \*, char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char těkavé \*, char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char \*těkavé , char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char \*těkavé , char, char)|
|_InterlockedCompareExchangePointer|\* neplatné _InterlockedCompareExchangePointer \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_acq|\* neplatné _InterlockedCompareExchangePointer_acq \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_nf|\* neplatné _InterlockedCompareExchangePointer_nf \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchangePointer_rel|\* neplatné _InterlockedCompareExchangePointer_rel \* \*(neplatné těkavé , neplatné \*, neplatné \*)|
|_InterlockedCompareExchange_acq|dlouhé _InterlockedCompareExchange_acq (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedCompareExchange_nf|dlouhé _InterlockedCompareExchange_nf (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedCompareExchange_rel|dlouhé _InterlockedCompareExchange_rel (dlouhé těkavé \*, dlouhé, dlouhé)|
|_InterlockedDecrement|dlouhé __cdecl _InterlockedDecrement \*(dlouhé těkavé )|
|_InterlockedDecrement16|krátké _InterlockedDecrement16 (krátké těkavé \*)|
|_InterlockedDecrement16_acq|krátké _InterlockedDecrement16_acq (krátké těkavé \*)|
|_InterlockedDecrement16_nf|krátké _InterlockedDecrement16_nf (krátké těkavé \*)|
|_InterlockedDecrement16_rel|krátké _InterlockedDecrement16_rel (krátké těkavé \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf(\_ \*_int64 volatilní )|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel(\_ \*_int64 volatilní )|
|_InterlockedDecrement_acq|dlouhé _InterlockedDecrement_acq (dlouhé těkavé \*)|
|_InterlockedDecrement_nf|dlouhé _InterlockedDecrement_nf (dlouhé těkavé \*)|
|_InterlockedDecrement_rel|dlouhé _InterlockedDecrement_rel (dlouhé těkavé \*)|
|_InterlockedExchange|dlouhé __cdecl _InterlockedExchange \* (dlouhé těkavé _Target, dlouhé)|
|_InterlockedExchange16|krátké _InterlockedExchange16 (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange16_acq|krátké _InterlockedExchange16_acq (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange16_nf|krátké _InterlockedExchange16_nf (krátké těkavé \* _Target, krátké)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\_ \* _int64 \_volatilní _Target, _int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char těkavé \* _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char těkavé \* _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char těkavé \* _Target, char)|
|_InterlockedExchangeAdd|dlouhý __cdecl _InterlockedExchangeAdd \*(dlouhý těkavý, dlouhý)|
|_InterlockedExchangeAdd16|krátké _InterlockedExchangeAdd16 (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_acq|krátké _InterlockedExchangeAdd16_acq (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_nf|krátké _InterlockedExchangeAdd16_nf (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd16_rel|krátké _InterlockedExchangeAdd16_rel (krátké těkavé, \*krátké)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedExchangeAdd64_acq|_InterlockedExchangeAdd64_acq __int64(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char \*těkavé , char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char \*těkavé , char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char \*těkavé , char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char \*těkavé , char)|
|_InterlockedExchangeAdd_acq|dlouhé _InterlockedExchangeAdd_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangeAdd_nf|dlouhé _InterlockedExchangeAdd_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangeAdd_rel|dlouhé _InterlockedExchangeAdd_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedExchangePointer|neplatné \* _InterlockedExchangePointer \* \* (neplatné \*těkavé _Target, void )|
|_InterlockedExchangePointer_acq|neplatné \* _InterlockedExchangePointer_acq \* \* (neplatné \*těkavé _Target, void )|
|_InterlockedExchangePointer_nf|neplatné \* _InterlockedExchangePointer_nf \* \* (neplatné \*těkavé _Target, neplatné )|
|_InterlockedExchange_acq|dlouhé _InterlockedExchange_acq (dlouhé těkavé \* _Target, dlouhé)|
|_InterlockedExchange_nf|dlouhé _InterlockedExchange_nf (dlouhé těkavé \* _Target, dlouhé)|
|_InterlockedIncrement|dlouhé __cdecl _InterlockedIncrement \*(dlouhé těkavé )|
|_InterlockedIncrement16|krátké _InterlockedIncrement16 (krátké těkavé \*)|
|_InterlockedIncrement16_acq|krátké _InterlockedIncrement16_acq (krátké těkavé \*)|
|_InterlockedIncrement16_nf|krátké _InterlockedIncrement16_nf (krátké těkavé \*)|
|_InterlockedIncrement16_rel|krátké _InterlockedIncrement16_rel (krátké těkavé \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\_ \*_int64 volatilní )|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel(\_ \*_int64 volatilní )|
|_InterlockedIncrement_acq|dlouhé _InterlockedIncrement_acq (dlouhé těkavé \*)|
|_InterlockedIncrement_nf|dlouhé _InterlockedIncrement_nf (dlouhé těkavé \*)|
|_InterlockedIncrement_rel|dlouhé _InterlockedIncrement_rel (dlouhé těkavé \*)|
|_InterlockedOr|dlouhé _InterlockedOr (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr16|krátké _InterlockedOr16 (krátké těkavé, \*krátké)|
|_InterlockedOr16_acq|krátké _InterlockedOr16_acq (krátké těkavé, \*krátké)|
|_InterlockedOr16_nf|krátké _InterlockedOr16_nf (krátké těkavé, \*krátké)|
|_InterlockedOr16_rel|krátké _InterlockedOr16_rel (krátké těkavé, \*krátké)|
|_InterlockedOr64|__int64 _InterlockedOr64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedOr8|char _InterlockedOr8 (char těkavé \*, char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char těkavé \*, char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char těkavé \*, char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char \*těkavé , char)|
|_InterlockedOr_acq|dlouhé _InterlockedOr_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr_nf|dlouhé _InterlockedOr_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedOr_rel|dlouhé _InterlockedOr_rel (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor|dlouhé _InterlockedXor (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor16|krátké _InterlockedXor16 (krátké těkavé, \*krátké)|
|_InterlockedXor16_acq|krátké _InterlockedXor16_acq (krátké těkavé, \*krátké)|
|_InterlockedXor16_nf|krátké _InterlockedXor16_nf (krátké těkavé, \*krátké)|
|_InterlockedXor16_rel|krátké _InterlockedXor16_rel (krátké těkavé, \*krátké)|
|_InterlockedXor64|__int64 _InterlockedXor64(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq(\_ \*_int64 \_volatilní, _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel(\_ \*_int64 \_volatilní , _int64)|
|_InterlockedXor8|char _InterlockedXor8(char \*těkavé , char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char \*těkavé , char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char \*těkavé , char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char \*těkavé , char)|
|_InterlockedXor_acq|dlouhé _InterlockedXor_acq (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor_nf|dlouhé _InterlockedXor_nf (dlouhé těkavé \*, dlouhé)|
|_InterlockedXor_rel|dlouhé _InterlockedXor_rel (dlouhé těkavé \*, dlouhé)|

[Návrat[na vrchol](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest vnitřní chod

Prostý interlocked bit test vnitřní jsou společné pro všechny platformy. ARM `_acq`přidává `_rel`, `_nf` a varianty, které právě upravit bariérovou sémantiku operace, jak je popsáno v [_nf (bez plotu) příponu](#nf_suffix) dříve v tomto článku.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_interlockedbittestandreset|nepodepsané char _interlockedbittestandreset \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_acq|nepodepsané char _interlockedbittestandreset_acq \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_nf|nepodepsané char _interlockedbittestandreset_nf \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandreset_rel|nepodepsané char _interlockedbittestandreset_rel \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset|nepodepsané char _interlockedbittestandset \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_acq|nepodepsané char _interlockedbittestandset_acq \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_nf|nepodepsané char _interlockedbittestandset_nf \*(dlouhé těkavé , dlouhé)|
|_interlockedbittestandset_rel|nepodepsané char _interlockedbittestandset_rel \*(dlouhé těkavé , dlouhé)|

[Návrat[na vrchol](#top)]

## <a name="see-also"></a>Viz také

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[ARM64 vnitřní objekty](arm64-intrinsics.md)\
[Arm assembler odkaz](../assembler/arm/arm-assembler-reference.md)\
[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)
