---
title: ARM – vnitřní prvky
ms.date: 11/04/2016
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
- cl.exe compiler, intrinsics
- intrinsics, ARM
ms.assetid: d3d7dadd-7bd5-4508-8bff-371a66913e20
ms.openlocfilehash: 47fd2f449568494bafde993e035d3ec37c44f6fe
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027624"
---
# <a name="arm-intrinsics"></a>ARM – vnitřní prvky

Kompilátor Visual C++ zpřístupňuje následující vnitřní objekty na architekturu ARM. Další informace o ARM najdete v článku [příručky pro referenční architekturu ARM](http://go.microsoft.com/fwlink/p/?LinkId=522049) a [příručka nástroje assembleru ARM](http://go.microsoft.com/fwlink/p/?LinkId=246102) na webu informační středisko ARM.

##  <a name="top"></a> NEON

Rozšíření sady instrukcí vektorů NEON ARM poskytují možnosti více dat jedné instrukce (SIMD), které se podobají těm v MMX a SSE vektoru instrukce sady, které jsou společné pro procesory s architekturou x86 a x64.

Vnitřní objekty NEON jsou podporovány, jak je uvedeno v souboru hlaviček `arm_neon.h`. Podpora kompilátoru Visual C++ pro vnitřní objekty NEON vypadá podobně jako u kompilátoru ARM, které jsou uvedené v dodatku G [sada nástrojů kompilátoru ARM, verze 4.1 kompilátoru odkaz](http://go.microsoft.com/fwlink/p/?LinkId=251083) na webu informační středisko ARM.

Hlavní rozdíl mezi kompilátor Visual C++ a kompilátor ARM je, že kompilátor Visual C++ přidá `_ex` varianty `vldX` a `vstX` vektorové načtení a uložení pokyny. `_ex` Varianty trvat další parametr, který určuje zarovnání argument ukazatele, ale jsou jinak stejné jako jejich jinou hodnotu než`_ex` protějšky.

##  <a name="A"></a> Vnitřní objekty ARM specifické výpis

|Název funkce|Instrukce|Prototyp funkce|
|-------------------|-----------------|------------------------|
|_arm_smlal|SMLAL|__int64 _arm_smlal (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_umlal|UMLAL|unsigned __int64 _arm_umlal (unsigned \__int64 _RdHiLo, _Rn unsigned int, unsigned int _Rm)|
|_arm_clz|CLZ|_arm_clz int bez znaménka (unsigned int _Rm)|
|_arm_qadd|QADD|int _arm_qadd (int _Rm, int _Rn)|
|_arm_qdadd|QDADD|int _arm_qdadd (int _Rm, int _Rn)|
|_arm_qdsub|QDSUB|int _arm_qdsub (int _Rm, int _Rn)|
|_arm_qsub|QSUB|int _arm_qsub (int _Rm, int _Rn)|
|_arm_smlabb|SMLABB|int _arm_smlabb (int _Rn, int _Rm, int _Ra)|
|_arm_smlabt|SMLABT|int _arm_smlabt (int _Rn, int _Rm, int _Ra)|
|_arm_smlatb|SMLATB|int _arm_smlatb (int _Rn, int _Rm, int _Ra)|
|_arm_smlatt|SMLATT|int _arm_smlatt (int _Rn, int _Rm, int _Ra)|
|_arm_smlalbb|SMLALBB|__int64 _arm_smlalbb (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlalbt|SMLALBT|__int64 _arm_smlalbt (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlaltb|SMLALTB|__int64 _arm_smlaltb (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlaltt|SMLALTT|__int64 _arm_smlaltt (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlawb|SMLAWB|int _arm_smlawb (int _Rn, int _Rm, int _Ra)|
|_arm_smlawt|SMLAWT|int _arm_smlawt (int _Rn, int _Rm, int _Ra)|
|_arm_smulbb|SMULBB|int _arm_smulbb (int _Rn, int _Rm)|
|_arm_smulbt|SMULBT|int _arm_smulbt (int _Rn, int _Rm)|
|_arm_smultb|SMULTB|int _arm_smultb (int _Rn, int _Rm)|
|_arm_smultt|SMULTT|int _arm_smultt (int _Rn, int _Rm)|
|_arm_smulwb|SMULWB|int _arm_smulwb (int _Rn, int _Rm)|
|_arm_smulwt|SMULWT|int _arm_smulwt (int _Rn, int _Rm)|
|_arm_sadd16|SADD16|int _arm_sadd16 (_Rn int, int _Rm)|
|_arm_sadd8|SADD8|int _arm_sadd8 (_Rn int, int _Rm)|
|_arm_sasx|SASX|int _arm_sasx (int _Rn, int _Rm)|
|_arm_ssax|SSAX|int _arm_ssax (int _Rn, int _Rm)|
|_arm_ssub16|SSUB16|int _arm_ssub16 (_Rn int, int _Rm)|
|_arm_ssub8|SSUB8|int _arm_ssub8 (_Rn int, int _Rm)|
|_arm_shadd16|SHADD16|int _arm_shadd16 (_Rn int, int _Rm)|
|_arm_shadd8|SHADD8|int _arm_shadd8 (_Rn int, int _Rm)|
|_arm_shasx|SHASX|int _arm_shasx (int _Rn, int _Rm)|
|_arm_shsax|SHSAX|int _arm_shsax (int _Rn, int _Rm)|
|_arm_shsub16|SHSUB16|int _arm_shsub16 (_Rn int, int _Rm)|
|_arm_shsub8|SHSUB8|int _arm_shsub8 (_Rn int, int _Rm)|
|_arm_qadd16|QADD16|int _arm_qadd16 (_Rn int, int _Rm)|
|_arm_qadd8|QADD8|int _arm_qadd8 (_Rn int, int _Rm)|
|_arm_qasx|QASX|int _arm_qasx (int _Rn, int _Rm)|
|_arm_qsax|QSAX|int _arm_qsax (int _Rn, int _Rm)|
|_arm_qsub16|QSUB16|int _arm_qsub16 (_Rn int, int _Rm)|
|_arm_qsub8|QSUB8|int _arm_qsub8 (_Rn int, int _Rm)|
|_arm_uadd16|UADD16|unsigned int _arm_uadd16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uadd8|UADD8|unsigned int _arm_uadd8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uasx|UASX|unsigned int _arm_uasx (_Rn unsigned int, unsigned int _Rm)|
|_arm_usax|USAX|unsigned int _arm_usax (_Rn unsigned int, unsigned int _Rm)|
|_arm_usub16|USUB16|unsigned int _arm_usub16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_usub8|USUB8|unsigned int _arm_usub8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhadd16|UHADD16|unsigned int _arm_uhadd16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhadd8|UHADD8|unsigned int _arm_uhadd8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhasx|UHASX|unsigned int _arm_uhasx (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhsax|UHSAX|unsigned int _arm_uhsax (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhsub16|UHSUB16|unsigned int _arm_uhsub16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uhsub8|UHSUB8|unsigned int _arm_uhsub8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqadd16|UQADD16|unsigned int _arm_uqadd16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqadd8|UQADD8|unsigned int _arm_uqadd8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqasx|UQASX|unsigned int _arm_uqasx (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqsax|UQSAX|unsigned int _arm_uqsax (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqsub16|UQSUB16|unsigned int _arm_uqsub16 (_Rn unsigned int, unsigned int _Rm)|
|_arm_uqsub8|UQSUB8|unsigned int _arm_uqsub8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_sxtab|SXTAB|int _arm_sxtab (int _Rn, int _Rm, unsigned int _Rotation)|
|_arm_sxtab16|SXTAB16|int _arm_sxtab16 (_Rn int, int _Rm, unsigned int _Rotation)|
|_arm_sxtah|SXTAH|int _arm_sxtah (int _Rn, int _Rm, unsigned int _Rotation)|
|_arm_uxtab|UXTAB|_arm_uxtab int bez znaménka (unsigned int _Rn, _Rm unsigned int, unsigned int _Rotation)|
|_arm_uxtab16|UXTAB16|unsigned int _arm_uxta16b (unsigned int _Rn, _Rm unsigned int, unsigned int _Rotation)|
|_arm_uxtah|UXTAH|_arm_uxtah int bez znaménka (unsigned int _Rn, _Rm unsigned int, unsigned int _Rotation)|
|_arm_sxtb|SXTB|int _arm_sxtb (int _Rn, unsigned int _Rotation)|
|_arm_sxtb16|SXTB16|int _arm_sxtb16 (_Rn int, unsigned int _Rotation)|
|_arm_sxth|SXTH|int _arm_sxth (int _Rn, unsigned int _Rotation)|
|_arm_uxtb|UXTB|unsigned int _arm_uxtb (_Rn unsigned int, unsigned int _Rotation)|
|_arm_uxtb16|UXTB16|unsigned int _arm_uxtb16 (_Rn unsigned int, unsigned int _Rotation)|
|_arm_uxth|UXTH|unsigned int _arm_uxth (_Rn unsigned int, unsigned int _Rotation)|
|_arm_pkhbt|PKHBT|int _arm_pkhbt (int _Rn, int _Rm, unsigned int _Lsl_imm)|
|_arm_pkhtb|PKHTB|int _arm_pkhtb (int _Rn, int _Rm, unsigned int _Asr_imm)|
|_arm_usad8|USAD8|unsigned int _arm_usad8 (_Rn unsigned int, unsigned int _Rm)|
|_arm_usada8|USADA8|unsigned int _arm_usada8 (unsigned int _Rn, _Rm unsigned int, unsigned int _Ra)|
|_arm_ssat|SSAT|int _arm_ssat (unsigned int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, unsigned int _Shift_imm)|
|_arm_usat|USAT|int _arm_usat (unsigned int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, unsigned int _Shift_imm)|
|_arm_ssat16|SSAT16|int _arm_ssat16 (unsigned int _Sat_imm, _int _Rn)|
|_arm_usat16|USAT16|int _arm_usat16 (unsigned int _Sat_imm, _int _Rn)|
|_arm_rev|REV|_arm_rev int bez znaménka (unsigned int _Rm)|
|_arm_rev16|REV16|unsigned int _arm_rev16 (unsigned int _Rm)|
|_arm_revsh|REVSH|_arm_revsh int bez znaménka (unsigned int _Rm)|
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
|_arm_smlald|SMLALD|__int64 _arm_smlald (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlaldx|SMLALDX|__int64 _arm_smlaldx (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlsld|SMLSLD|__int64 _arm_smlsld (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smlsldx|SMLSLDX|__int64 _arm_smlsldx (\__int64 _RdHiLo int _Rn, int _Rm)|
|_arm_smuad|SMUAD|int _arm_smuad (int _Rn, int _Rm)|
|_arm_smuadx|SMUADX|int _arm_muadxs (int _Rn, int _Rm)|
|_arm_smusd|SMUSD|int _arm_smusd (int _Rn, int _Rm)|
|_arm_smusdx|SMUSDX|int _arm_smusdx (int _Rn, int _Rm)|
|_arm_smull|SMULL|__int64 _arm_smull (int _Rn, int _Rm)|
|_arm_umull|UMULL|unsigned __int64 _arm_umull (_Rn unsigned int, unsigned int _Rm)|
|_arm_umaal|UMAAL|unsigned __int64 _arm_umaal (_RdLo unsigned int, unsigned int _RdHi, _Rn unsigned int, unsigned int _Rm)|
|_arm_bfc|BFC|_arm_bfc int bez znaménka (unsigned int _Rd, _Lsb unsigned int, unsigned int k vlastnostem _Width)|
|_arm_bfi|BFI|unsigned int _arm_bfi (_Rd unsigned int, unsigned int _Rn, _Lsb unsigned int, unsigned int k vlastnostem _Width)|
|_arm_rbit|RBIT|_arm_rbit int bez znaménka (unsigned int _Rm)|
|_arm_sbfx|SBFX|int _arm_sbfx (int _Rn, unsigned int _Lsb, k vlastnostem _Width unsigned int)|
|_arm_ubfx|UBFX|_arm_ubfx int bez znaménka (unsigned int _Rn, _Lsb unsigned int, unsigned int k vlastnostem _Width)|
|_arm_sdiv|SDIV|int _arm_sdiv (int _Rn, int _Rm)|
|_arm_udiv|UDIV|unsigned int _arm_udiv (_Rn unsigned int, unsigned int _Rm)|
|__cps|CPS|void __cps (unsigned int _Ops, _Flags unsigned int, unsigned int reži_m)|
|__dmb|DMB|void __dmb (unsigned int `_Type`)<br /><br /> Vloží operaci barrier paměti do datového proudu instrukce. Parametr `_Type` určuje druh omezení, které je vynucuje odbourejte překážky bránící.<br /><br /> Další informace o druzích omezení, které je možné vynutit, najdete v části [omezení paměti Barrier](#BarrierRestrictions).|
|__dsb|DSB|void __dsb (unsigned int _typ)<br /><br /> Vloží operaci barrier paměti do datového proudu instrukce. Parametr `_Type` určuje druh omezení, které je vynucuje odbourejte překážky bránící.<br /><br /> Další informace o druzích omezení, které je možné vynutit, najdete v části [omezení paměti Barrier](#BarrierRestrictions).|
|__isb|ISB|void __isb (unsigned int _typ)<br /><br /> Vloží operaci barrier paměti do datového proudu instrukce. Parametr `_Type` určuje druh omezení, které je vynucuje odbourejte překážky bránící.<br /><br /> Další informace o druzích omezení, které je možné vynutit, najdete v části [omezení paměti Barrier](#BarrierRestrictions).|
|__emit||void __emit (unsigned \__int32 opcode)<br /><br /> Vloží zadaný instrukce na datový proud instrukcí výstupní kompilátorem.<br /><br /> Hodnota `opcode` musí být konstantní výraz, který je známý v době kompilace. Velikost word instrukce je 16 bitů a nejdůležitější 16 bitů `opcode` jsou ignorovány.<br /><br /> Kompilátor nesnaží interpretovat obsah `opcode` a před provedením vložené instrukce nezaručuje stavu procesoru nebo paměti.<br /><br /> Kompilátor předpokládá, že stav procesoru a paměti jsou beze změny po provedení vložené instrukce. Pokyny, které mění stav proto může mít nepříznivý vliv na běžné kód, který je generovaný kompilátorem.<br /><br /> Z tohoto důvodu použít `emit` pouze pro vložení instrukcí, které ovlivňují stav procesoru, který kompilátor nezpracovává obvykle – například koprocesoru stavu – nebo k implementaci funkcí, které jsou deklarovány pomocí `declspec(naked)`.|
|__hvc|HVC|__hvc int bez znaménka (unsigned int,...).|
|__iso_volatile_load16||__int16 \__iso_volatile_load16(const volatile \__int16 \*)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32(const volatile \__int32 \*)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64(const volatile \__int64 \*)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16(volatile \__int16 \*, \__int16)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32(volatile \__int32 \*, \__int32)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64(volatile \__int64 \*, \__int64)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8(volatile \__int8 \*, \__int8)<br /><br /> Další informace najdete v tématu [Using __iso_volatile_load/store instrinsics](#IsoVolatileLoadStore).|
|__ldrexd|LDREXD|__int64 \__ldrexd(const volatile \__int64 \*)|
|__prefetch|PLD|void __cdecl \__prefetch(const void \*)<br /><br /> Poskytuje `PLD` paměti pokyn k systému, tato paměť na nebo blízko ní zadaná adresa přístupná brzy. Některé systémy rozhodnout optimalizovat pro tento vzor přístupu paměti pro zvýšení výkonu modulu runtime. Však z C++ language pohledu, funkce nemá žádný vliv pozorovatelné a může nedělat nic vůbec.|
|__rdpmccntr64||unsigned __int64 \__rdpmccntr64(void)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert(int, const char \*)|
|__swi|SVC|__swi int bez znaménka (unsigned int,...).|
|__trap|BKPT|int __trap (int,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|_AddSatInt|QADD|int _AddSatInt (int, int)|
|_CopyDoubleFromInt64||dvojité _CopyDoubleFromInt64 (\__int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32(\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||unsigned int _CountLeadingOnes64 (unsigned \__int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64 (\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||unsigned int _CountLeadingZeros64 (unsigned \__int64)|
|_CountOneBits||unsigned int _CountOneBits(unsigned long)|
|_CountOneBits64||unsigned int _CountOneBits64 (unsigned \__int64)|
|_DAddSatInt|QDADD|int _DAddSatInt (int, int)|
|_DSubSatInt|QDSUB|int _DSubSatInt (int, int)|
|_isunordered||int _isunordered (double, double)|
|_isunorderedf||int _isunorderedf(float, float)|
|_MoveFromCoprocessor|MRC|_MoveFromCoprocessor int bez znaménka (unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveFromCoprocessor _MoveFromCoprocessor2](#MoveFromCo).|
|_MoveFromCoprocessor2|MRC2|unsigned int _MoveFromCoprocessor2 (unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveFromCoprocessor _MoveFromCoprocessor2](#MoveFromCo).|
|_MoveFromCoprocessor64|MRRC|unsigned __int64 _MoveFromCoprocessor64 (unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveFromCoprocessor64](#MoveFromCo64).|
|_MoveToCoprocessor|MCR|void _MoveToCoprocessor (unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveToCoprocessor _MoveToCoprocessor2](#MoveToCo).|
|_MoveToCoprocessor2|MCR2|void _MoveToCoprocessor2 (unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveToCoprocessor _MoveToCoprocessor2](#MoveToCo).|
|_MoveToCoprocessor64|MCRR|void _MoveToCoprocessor64 (unsigned \__int64, unsigned int, unsigned int, unsigned int)<br /><br /> Čte data z koprocesoru ARM pomocí pokynů pro přenos dat koprocesoru. Další informace najdete v části [_MoveToCoprocessor64](#MoveToCo64).|
|_MulHigh||dlouhé _MulHigh (long, long)|
|_MulUnsignedHigh||unsigned long _MulUnsignedHigh (long long bez znaménka, bez znaménka)|
|_ReadBankedReg|MRS|int _ReadBankedReg (int _Reg)|
|_ReadStatusReg|MRS|int _ReadStatusReg(int)|
|_SubSatInt|QSUB|int _SubSatInt (int, int)|
|_WriteBankedReg|MSR|void _WriteBankedReg (int _Value, int _Reg)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, int, int)|

[[NEON](#top)]

###  <a name="BarrierRestrictions"></a> Omezení paměti Barrier

Vnitřní funkce `__dmb` (data paměti barrier), `__dsb` (barrier synchronizaci dat), a `__isb` (instrukce synchronizace barrier) použijte následující předdefinované hodnoty k určení barrier omezení paměti v podmínkách sdílení domény a druh přístupu, které jsou ovlivněny operaci.

|Hodnota omezení|Popis|
|-----------------------|-----------------|
|_ARM_BARRIER_SY|Úplnou, čtení a zápisy.|
|_ARM_BARRIER_ST|Úplné systém zapíše pouze.|
|_ARM_BARRIER_ISH|Vnitřní, které se dají sdílet, čtení a zápisu.|
|_ARM_BARRIER_ISHST|Vnitřní sdílet, zapíše pouze.|
|_ARM_BARRIER_NSH|Jiné – které se dají sdílet, čtení a zápisu.|
|_ARM_BARRIER_NSHST|Pouze bez sdílet, zápisy.|
|_ARM_BARRIER_OSH|Vnější sdílet, čtení a zápisu.|
|_ARM_BARRIER_OSHST|Vnější sdílet, zapíše pouze.|

Pro `__isb` vnitřní, je jediným omezením, který je aktuálně platný _ARM_BARRIER_SY; všechny ostatní hodnoty jsou vyhrazené architekturu.

###  <a name="IsoVolatileLoadStore"></a> instrinsics Using __iso_volatile_load/store

Tyto vnitřní funkce explicitně provádět zatížení a úložišť, která nejsou v souladu s optimalizace kompilátoru.

```
__int16 __iso_volatile_load16(const volatile __int16 * Location)
__int32 __iso_volatile_load32(const volatile __int32 * Location)
__int64 __iso_volatile_load64(const volatile __int64 * Location)
__int8 __iso_volatile_load8(const volatile __int8 * Location)

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value)
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value)
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value)
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value)
```

#### <a name="parameters"></a>Parametry

*Poloha*<br/>
Adresa umístění v paměti a číst nebo zapisovat.

*Hodnota*<br/>
Hodnota k zápisu na zadaném umístění v paměti (pouze vnitřních úložiště objektů).

#### <a name="return-value-load-intrinsics-only"></a>Vrátí hodnotu (pouze pro zatížení vnitřní)

Hodnota umístění v paměti, která je zadána `Location`.

#### <a name="remarks"></a>Poznámky

Můžete použít `__iso_volatile_load8/16/32/64` a `__iso_volatile_store8/16/32/64` vnitřní objekty explicitně provádět přístupy do paměti, které nejsou v souladu s optimalizace kompilátoru. Kompilátor nelze odebrat, synthetize, nebo změňte relativní pořadí těchto operací, ale negeneruje implicitní hardwarové překážky paměti. Proto hardwaru může stále změnit pořadí přístupu k pozorovatelných paměti napříč více vlákny. Přesněji řečeno, tyto vnitřní objekty jsou ekvivalentní s následující výrazy zkompilovat v rámci **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Všimněte si, že vnitřní objekty trvat ukazatelé typu volatile tak, aby vyhovovaly volatile proměnné. Neexistuje však žádný požadavek nebo doporučení pro použití jako argumenty; ukazatelé typu volatile Sémantika tyto operace se přesně shodují-li regulární, není typu volatile. typ se používá.

Další informace o **/volatile:iso** argument příkazového řádku, naleznete v tématu [/volatile (interpretace klíčového slova volatile)](../build/reference/volatile-volatile-keyword-interpretation.md).

###  <a name="MoveFromCo"></a> _MoveFromCoprocessor, _MoveFromCoprocessor2

Tyto vnitřní funkce podle pokynů pro přenos dat koprocesoru číst data z ARM coprocessors.

```
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

*coproc*<br/>
Koprocesor číslo v rozsahu 0 až 15.

*opcode1*<br/>
Koprocesor konkrétní operační kód v rozsahu 0 až 7

*crn*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje první operand podle pokynů.

*crm*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje další zdrojové nebo cílové operand.

*opcode2*<br/>
Další specifické pro koprocesor operační kód v rozsahu 0 až 7.

#### <a name="return-value"></a>Návratová hodnota

Hodnota, která je načtena z 80bitové.

#### <a name="remarks"></a>Poznámky

Hodnoty všech parametrů pět tomto vnitřních musí být konstantní výrazy, které jsou v době kompilace znám.

`_MoveFromCoprocessor` použije instrukce MRC; `_MoveFromCoprocessor2` používá MRC2. Parametry odpovídají bitová pole, která jsou kódovány přímo do aplikace word instrukce. Výklad parametry závisí na koprocesoru. Další informace naleznete v příručce pro koprocesor dotyčný.

###  <a name="MoveFromCo64"></a> _MoveFromCoprocessor64

Pomocí pokynů pro přenos dat koprocesoru čte data z ARM coprocessors.

```
unsigned __int64 _MoveFromCoprocessor64(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>Parametry

*coproc*<br/>
Koprocesor číslo v rozsahu 0 až 15.

*opcode1*<br/>
Koprocesor konkrétní operační kód v rozsahu 0 až 15.

*crm*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje další zdrojové nebo cílové operand.

**Vrací hodnotu**

Hodnota, která je načtena z 80bitové.

#### <a name="remarks"></a>Poznámky

Hodnoty všech tří parametrů tomto vnitřních musí být konstantní výrazy, které jsou v době kompilace znám.

`_MoveFromCoprocessor64` používá MRRC instrukce. Parametry odpovídají bitová pole, která jsou kódovány přímo do aplikace word instrukce. Výklad parametry závisí na koprocesoru. Další informace naleznete v příručce pro koprocesor dotyčný.

###  <a name="MoveToCo"></a> _MoveToCoprocessor, _MoveToCoprocessor2

Tyto vnitřní funkce zapisovat data do ARM coprocessors pomocí pokynů koprocesoru data přenosu.

```
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

*value*<br/>
Hodnota má být proveden zápis 80bitové.

*coproc*<br/>
Koprocesor číslo v rozsahu 0 až 15.

*opcode1*<br/>
Koprocesor konkrétní operační kód v rozsahu 0 až 7.

*crn*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje první operand podle pokynů.

*crm*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje další zdrojové nebo cílové operand.

*opcode2*<br/>
Další specifické pro koprocesor operační kód v rozsahu 0 až 7.

#### <a name="return-value"></a>Návratová hodnota

Žádné

#### <a name="remarks"></a>Poznámky

Hodnoty `coproc`, `opcode1`, `crn`, `crm`, a `opcode2` parametry tomto vnitřních musí být konstantní výrazy, které jsou v době kompilace znám.

`_MoveToCoprocessor` použije instrukce MCR; `_MoveToCoprocessor2` používá MCR2. Parametry odpovídají bitová pole, která jsou kódovány přímo do aplikace word instrukce. Výklad parametry závisí na koprocesoru. Další informace naleznete v příručce pro koprocesor dotyčný.

###  <a name="MoveToCo64"></a> _MoveToCoprocessor64

Tyto vnitřní funkce zapisovat data do ARM coprocessors pomocí pokynů koprocesoru data přenosu.

```
void _MoveFromCoprocessor64(
      unsigned __int64 value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>Parametry

*coproc*<br/>
Koprocesor číslo v rozsahu 0 až 15.

*opcode1*<br/>
Koprocesor konkrétní operační kód v rozsahu 0 až 15.

*crm*<br/>
Koprocesor zaregistrovat číslo v rozsahu 0 až 15, který určuje další zdrojové nebo cílové operand.

#### <a name="return-value"></a>Návratová hodnota

Žádné

#### <a name="remarks"></a>Poznámky

Hodnoty `coproc`, `opcode1`, a `crm` parametry tomto vnitřních musí být konstantní výrazy, které jsou v době kompilace znám.

`_MoveFromCoprocessor64` používá MCRR instrukce. Parametry odpovídají bitová pole, která jsou kódovány přímo do aplikace word instrukce. Výklad parametry závisí na koprocesoru. Další informace naleznete v příručce pro koprocesor dotyčný.

##  <a name="I"></a> Podpora ARM pro vnitřní objekty z jiných architektury

Následující tabulka obsahuje seznam vnitřních objektů z jiné architektury, které jsou podporovány na platformách ARM. Kde se liší od jeho chování pro jiné architektury hardwaru chování vnitřní na ARM jsou uvedené další podrobnosti.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|void __cdecl \__debugbreak(void)|
|__fastfail|__declspec(noreturn) void \__fastfail (unsigned int).|
|__nop|void __nop(void) **Poznámka:**  Na platformách ARM tato funkce generuje NOP instrukce, pokud jeden je implementovaná v cílové architektuře; v opačném případě je vygenerována alternativní instrukce, která se nezmění stav programu nebo využití procesoru – například `MOV r8, r8`. Toto je funkčně srovnatelný s \__nop vnitřní pro jiné architektury hardwaru. Protože pokyn, který nemá žádný vliv na stav aplikace nebo procesor může ignorovat. Cílová architektura jako optimalizace, instrukce nespotřebovává nutně cyklů procesoru. Proto nepoužívejte \__nop vnitřní k manipulaci s doba provádění sekvenci kódu, pokud si nejste jisti, o jak procesoru se bude chovat. Místo toho můžete použít \__nop vnitřní zarovnat další instrukci k určité hranici 32-bit adrese.|
|__yield|void __yield(void) **Poznámka:**  Na platformách ARM, tato funkce generuje instrukce YIELD, což znamená, že vlákno provádí úlohu, která může být dočasně pozastaveno z spuštění – například spinlock – nemá žádný vliv na program. To umožňuje procesoru ke spuštění dalších úloh během provádění cykly, které by jinak byly ztraceny.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress(void)|
|_BitScanForward|unsigned char _BitScanForward (unsigned long \* _Index unsigned long _podsítě)|
|_BitScanReverse|unsigned char _BitScanReverse (unsigned long \* _Index unsigned long _podsítě)|
|_bittest|unsigned char _bittest (long const \*, long)|
|_bittestandcomplement|unsigned char _bittestandcomplement (long \*, long)|
|_bittestandreset|unsigned char _bittestandreset (long \*, long)|
|_bittestandset|unsigned char _bittestandset (long \*, long)|
|_byteswap_uint64|unsigned __int64 \__byteswap_uint64 – _cdecl (unsigned \__int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|_byteswap_ushort – unsigned short __cdecl (unsigned short)|
|_disable|void __cdecl _disable(void) **Poznámka:**  Na platformách ARM tato funkce generuje instrukce CPSID; je k dispozici pouze jako vnitřní.|
|_enable|void __cdecl _enable(void) **Poznámka:**  Na platformách ARM tato funkce generuje instrukce CPSIE; je k dispozici pouze jako vnitřní.|
|_lrotl|_lrotl – dlouhý __cdecl bez znaménka (unsigned long int)|
|_lrotr|_lrotr – dlouhý __cdecl bez znaménka (unsigned long int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress(void)|
|_rotl|_rotl – __cdecl int bez znaménka (_Value unsigned int, int _Shift)|
|_rotl16|unsigned short _rotl16 (unsigned short _Value, unsigned char _Shift)|
|_rotl64|unsigned __int64 \__rotl64 – _cdecl (unsigned \__int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8 (unsigned char _Value, unsigned char _Shift)|
|_rotr|_rotr – __cdecl int bez znaménka (_Value unsigned int, int _Shift)|
|_rotr16|unsigned short _rotr16 (unsigned short _Value, unsigned char _Shift)|
|_rotr64|unsigned __int64 \__rotr64 – _cdecl (unsigned \__int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8 (unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[NEON](#top)]

## <a name="interlocked-intrinsics"></a>Vnitřní funkce Interlocked

Propojené vnitřní objekty jsou sada vnitřních objektů, které jsou používány k provádění atomických operací čtení modify-write. Některé z nich jsou společné pro všechny platformy. Jsou uvedeny samostatně zde vzhledem k tomu, že existuje velký počet z nich, ale protože jejich definice jsou většinou redundantní, je snazší uvažovat o jejich obecné podmínky. Jejich názvy lze použít k odvození přesné chování.

Následující tabulka shrnuje podporu ARM – vnitřní prvky bez bittest propojené. Každá buňka tabulky odpovídá názvu, který je odvozen připojením názvu operace v buňce nejvíce vlevo řádku a název typu v nejvyšším buňky sloupce, který se `_Interlocked`. Například buňky v průsečíku `Xor` řádek a **8** sloupec odpovídá `_InterlockedXor8` a jsou plně podporovány. Většina funkcí podporovaných nabízejí tyto volitelné přípony: `_acq`, `_rel`, a `_nf`. `_acq` Přípona označuje "získat" sémantické a `_rel` přípona označuje "vydání" sémantické. `_nf` Nebo příponu "žádné ohrazení" je jedinečné pro ARM a je popsána v následující části.

||8|16|32|64|P|
|-|-------|--------|--------|--------|-------|
|Přidejte|Žádné|Žádný|Do bloku|Do bloku|Žádný|
|A|Do bloku|Do bloku|Do bloku|Do bloku|Žádný|
|CompareExchange|Do bloku|Do bloku|Do bloku|Do bloku|Do bloku|
|Snížení|Žádné|Do bloku|Do bloku|Do bloku|Žádný|
|Exchange|Částečné|Částečné|Částečné|Částečné|Částečné|
|ExchangeAdd|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|
|Přírůstek|Žádné|Do bloku|Do bloku|Do bloku|Žádné|
|Nebo|Do bloku|Do bloku|Do bloku|Do bloku|Žádný|
|XOR|Do bloku|Do bloku|Do bloku|Do bloku|Žádné|

Klíč:

- **Úplné**: podporuje prostý, `_acq`, `_rel`, a `_nf` formuláře.

- **Částečné**: podporuje prostý, `_acq`, a `_nf` formuláře.

- **Žádný**: Není podporováno

###  <a name="nf_suffix"></a> _nf (no fence) Suffix

`_nf` Nebo přípona "žádné ohrazení" označuje, že operace nechová jako jakýkoli druh barrier paměti. Tím se liší od tři formuláře (plain, `_acq`, a `_rel`), který všechny chovat jako určitého druhu bariéry. Jeden využití `_nf` formuláře je Udržovat statistiky čítače, která se aktualizuje pomocí více vláken ve stejnou dobu, ale jehož hodnota se jinak nepoužívá, přestože jsou provádění více vláken.

### <a name="list-of-interlocked-intrinsics"></a>Seznam vnitřních objektů Interlocked

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_InterlockedAdd|dlouhé _InterlockedAdd (long _volatile \*, long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq(\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAdd_acq|dlouhé _InterlockedAdd_acq (long volatile \*, long)|
|_InterlockedAdd_nf|dlouhé _InterlockedAdd_nf (long volatile \*, long)|
|_InterlockedAdd_rel|dlouhé _InterlockedAdd_rel (long volatile \*, long)|
|_InterlockedAnd|dlouhé _InterlockedAnd (long volatile \*, long)|
|_InterlockedAnd16|krátký _InterlockedAnd16 (krátký volatile \*, short)|
|_InterlockedAnd16_acq|krátký _InterlockedAnd16_acq (krátký volatile \*, short)|
|_InterlockedAnd16_nf|krátký _InterlockedAnd16_nf (krátký volatile \*, short)|
|_InterlockedAnd16_rel|krátký _InterlockedAnd16_rel (krátký volatile \*, short)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAnd8|Char _InterlockedAnd8 (char volatile \*, char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char volatile \*, char)|
|_InterlockedAnd8_nf|Char _InterlockedAnd8_nf (char volatile \*, char)|
|_InterlockedAnd8_rel|Char _InterlockedAnd8_rel (char volatile \*, char)|
|_InterlockedAnd_acq|dlouhé _InterlockedAnd_acq (long volatile \*, long)|
|_InterlockedAnd_nf|dlouhé _InterlockedAnd_nf (long volatile \*, long)|
|_InterlockedAnd_rel|dlouhé _InterlockedAnd_rel (long volatile \*, long)|
|_InterlockedCompareExchange|dlouhé __cdecl _InterlockedCompareExchange (dlouho volatile \*, long, dlouhý)|
|_InterlockedCompareExchange16|krátký _InterlockedCompareExchange16 (krátký volatile \*, krátký, short)|
|_InterlockedCompareExchange16_acq|short _InterlockedCompareExchange16_acq(short volatile \*, short, short)|
|_InterlockedCompareExchange16_nf|short _InterlockedCompareExchange16_nf(short volatile \*, short, short)|
|_InterlockedCompareExchange16_rel|krátký _InterlockedCompareExchange16_rel (krátký volatile \*, krátký, short)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64(\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq(\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf(\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel(\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|Char _InterlockedCompareExchange8 (char volatile \*, char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq(char volatile \*, char, char)|
|_InterlockedCompareExchange8_nf|Char _InterlockedCompareExchange8_nf (char volatile \*, char, char)|
|_InterlockedCompareExchange8_rel|Char _InterlockedCompareExchange8_rel (char volatile \*, char, char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq(void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchange_acq|dlouhé _InterlockedCompareExchange_acq (long volatile \*, long, dlouhý)|
|_InterlockedCompareExchange_nf|dlouhé _InterlockedCompareExchange_nf (long volatile \*, long, dlouhý)|
|_InterlockedCompareExchange_rel|dlouhé _InterlockedCompareExchange_rel (long volatile \*, long, dlouhý)|
|_InterlockedDecrement|long __cdecl _InterlockedDecrement(long volatile \*)|
|_InterlockedDecrement16|krátký _InterlockedDecrement16 (krátký volatile \*)|
|_InterlockedDecrement16_acq|short _InterlockedDecrement16_acq(short volatile \*)|
|_InterlockedDecrement16_nf|krátký _InterlockedDecrement16_nf (krátký volatile \*)|
|_InterlockedDecrement16_rel|krátký _InterlockedDecrement16_rel (krátký volatile \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\__int64 volatile \*)|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatile \*)|
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq(long volatile \*)|
|_InterlockedDecrement_nf|dlouhé _InterlockedDecrement_nf (long volatile \*)|
|_InterlockedDecrement_rel|dlouhé _InterlockedDecrement_rel (long volatile \*)|
|_InterlockedExchange|dlouhé __cdecl _InterlockedExchange (dlouho volatile \* _cíl, dlouhý)|
|_InterlockedExchange16|krátký _InterlockedExchange16 (krátký volatile \* _cíl krátký)|
|_InterlockedExchange16_acq|short _InterlockedExchange16_acq(short volatile \* _Target, short)|
|_InterlockedExchange16_nf|short _InterlockedExchange16_nf(short volatile \* _Target, short)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange8|Char _InterlockedExchange8 (char volatile \* _cíl, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq(char volatile \* _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf(char volatile \* _Target, char)|
|_InterlockedExchangeAdd|dlouhé __cdecl _InterlockedExchangeAdd (long volatile \*, long)|
|_InterlockedExchangeAdd16|krátký _InterlockedExchangeAdd16 (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_acq|krátký _InterlockedExchangeAdd16_acq (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_nf|krátký _InterlockedExchangeAdd16_nf (krátký volatile \*, short)|
|_InterlockedExchangeAdd16_rel|krátký _InterlockedExchangeAdd16_rel (krátký volatile \*, short)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq(\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd8|Char _InterlockedExchangeAdd8 (char volatile \*, char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char volatile \*, char)|
|_InterlockedExchangeAdd8_nf|Char _InterlockedExchangeAdd8_nf (char volatile \*, char)|
|_InterlockedExchangeAdd8_rel|Char _InterlockedExchangeAdd8_rel (char volatile \*, char)|
|_InterlockedExchangeAdd_acq|dlouhé _InterlockedExchangeAdd_acq (long volatile \*, long)|
|_InterlockedExchangeAdd_nf|dlouhé _InterlockedExchangeAdd_nf (long volatile \*, long)|
|_InterlockedExchangeAdd_rel|dlouhé _InterlockedExchangeAdd_rel (long volatile \*, long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _cíl void \*)|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq(void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _cíl void \*)|
|_InterlockedExchange_acq|long _InterlockedExchange_acq(long volatile \* _Target, long)|
|_InterlockedExchange_nf|dlouhé _InterlockedExchange_nf (dlouho volatile \* _cíl, dlouhý)|
|_InterlockedIncrement|long __cdecl _InterlockedIncrement(long volatile \*)|
|_InterlockedIncrement16|krátký _InterlockedIncrement16 (krátký volatile \*)|
|_InterlockedIncrement16_acq|short _InterlockedIncrement16_acq(short volatile \*)|
|_InterlockedIncrement16_nf|short _InterlockedIncrement16_nf(short volatile \*)|
|_InterlockedIncrement16_rel|short _InterlockedIncrement16_rel(short volatile \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64(\__int64 volatile \*)|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\__int64 volatile \*)|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\__int64 volatile \*)|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel(\__int64 volatile \*)|
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq(long volatile \*)|
|_InterlockedIncrement_nf|dlouhé _InterlockedIncrement_nf (long volatile \*)|
|_InterlockedIncrement_rel|dlouhé _InterlockedIncrement_rel (long volatile \*)|
|_InterlockedOr|dlouhé _InterlockedOr (long volatile \*, long)|
|_InterlockedOr16|krátký _InterlockedOr16 (krátký volatile \*, short)|
|_InterlockedOr16_acq|short _InterlockedOr16_acq(short volatile \*, short)|
|_InterlockedOr16_nf|krátký _InterlockedOr16_nf (krátký volatile \*, short)|
|_InterlockedOr16_rel|krátký _InterlockedOr16_rel (krátký volatile \*, short)|
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\__int64 volatile \*, \__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedOr8|Char _InterlockedOr8 (char volatile \*, char)|
|_InterlockedOr8_acq|Char _InterlockedOr8_acq (char volatile \*, char)|
|_InterlockedOr8_nf|Char _InterlockedOr8_nf (char volatile \*, char)|
|_InterlockedOr8_rel|Char _InterlockedOr8_rel (char volatile \*, char)|
|_InterlockedOr_acq|long _InterlockedOr_acq(long volatile \*, long)|
|_InterlockedOr_nf|dlouhé _InterlockedOr_nf (long volatile \*, long)|
|_InterlockedOr_rel|dlouhé _InterlockedOr_rel (long volatile \*, long)|
|_InterlockedXor|dlouhé _InterlockedXor (long volatile \*, long)|
|_InterlockedXor16|krátký _InterlockedXor16 (krátký volatile \*, short)|
|_InterlockedXor16_acq|short _InterlockedXor16_acq(short volatile \*, short)|
|_InterlockedXor16_nf|krátký _InterlockedXor16_nf (krátký volatile \*, short)|
|_InterlockedXor16_rel|krátký _InterlockedXor16_rel (krátký volatile \*, short)|
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq(\__int64 volatile \*, \__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedXor8|Char _InterlockedXor8 (char volatile \*, char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char volatile \*, char)|
|_InterlockedXor8_nf|Char _InterlockedXor8_nf (char volatile \*, char)|
|_InterlockedXor8_rel|Char _InterlockedXor8_rel (char volatile \*, char)|
|_InterlockedXor_acq|dlouhé _InterlockedXor_acq (long volatile \*, long)|
|_InterlockedXor_nf|dlouhé _InterlockedXor_nf (long volatile \*, long)|
|_InterlockedXor_rel|dlouhé _InterlockedXor_rel (long volatile \*, long)|

[[NEON](#top)]

### <a name="interlockedbittest-intrinsics"></a>_interlockedbittest vnitřních objektů

Vnitřní objekty prostý propojené bittest jsou společné pro všechny platformy. Přidá ARM `_acq`, `_rel`, a `_nf` varianty, které právě upravují sémantiku barrier operace, jak je popsáno v [přípony _nf (žádné ohrazení)](#nf_suffix) dříve v tomto článku.

|Název funkce|Prototyp funkce|
|-------------------|------------------------|
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset (long volatile \*, long)|
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq (long volatile \*, long)|
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf (long volatile \*, long)|
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel (long volatile \*, long)|
|_interlockedbittestandset|unsigned char _interlockedbittestandset (long volatile \*, long)|
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq (long volatile \*, long)|
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf (long volatile \*, long)|
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel (long volatile \*, long)|

[[NEON](#top)]

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Referenční dokumentace assembleru ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)