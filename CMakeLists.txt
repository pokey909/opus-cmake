cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

project(Opus VERSION 1.2.1)

add_library(opus
        STATIC
        opus/src/opus_multistream_decoder.c
        opus/src/opus_multistream.c
        opus/src/opus_encoder.c
        opus/celt/celt_encoder.c
        opus/celt/bands.c
        opus/celt/entcode.c
        opus/celt/entdec.c
        opus/celt/entenc.c
        opus/celt/mathops.c
        opus/celt/vq.c
        opus/celt/cwrs.c
        opus/celt/celt.c
        opus/celt/mdct.c
        opus/celt/kiss_fft.c
        opus/celt/bands.c
        opus/celt/pitch.c
        opus/celt/celt_lpc.c
        opus/celt/quant_bands.c
        opus/celt/laplace.c
        opus/celt/modes.c
        opus/celt/rate.c
        opus/silk/lin2log.c
        opus/silk/enc_API.c
        opus/silk/resampler.c
        opus/silk/resampler_private_IIR_FIR.c
        opus/silk/resampler_private_up2_HQ.c
        opus/silk/resampler_private_down_FIR.c
        opus/silk/resampler_private_AR2.c
        opus/silk/resampler_rom.c
        opus/silk/float/encode_frame_FLP.c
        opus/silk/gain_quant.c
        opus/silk/log2lin.c
        opus/silk/encode_pulses.c
        opus/silk/code_signs.c
        opus/silk/tables_pulses_per_block.c
        opus/silk/tables_other.c
        opus/silk/shell_coder.c
        opus/silk/encode_indices.c
        opus/silk/tables_LTP.c
        opus/silk/tables_pitch_lag.c
        opus/silk/NLSF_unpack.c
        opus/silk/tables_gain.c
        opus/silk/float/wrappers_FLP.c
        opus/silk/quant_LTP_gains.c
        opus/silk/VQ_WMat_EC.c
        opus/silk/NSQ.c
        opus/silk/LPC_analysis_filter.c
        opus/silk/NSQ_del_dec.c
        opus/silk/process_NLSFs.c
        opus/silk/NLSF2A.c
        opus/silk/bwexpander_32.c
        opus/silk/LPC_inv_pred_gain.c
        opus/silk/table_LSF_cos.c
        opus/silk/NLSF_encode.c
        opus/silk/NLSF_decode.c
        opus/silk/NLSF_stabilize.c
        opus/silk/sort.c
        opus/silk/NLSF_VQ_weights_laroia.c
        opus/silk/NLSF_del_dec_quant.c
        opus/silk/NLSF_VQ.c
        opus/silk/interpolate.c
        opus/silk/float/wrappers_FLP.c
        opus/silk/A2NLSF.c
        opus/silk/float/process_gains_FLP.c
        opus/silk/float/find_pred_coefs_FLP.c
        opus/silk/float/residual_energy_FLP.c
        opus/silk/float/energy_FLP.c
        opus/silk/float/LPC_analysis_filter_FLP.c
        opus/silk/float/find_LPC_FLP.c
        opus/silk/float/burg_modified_FLP.c
        opus/silk/float/inner_product_FLP.c
        opus/silk/float/scale_copy_vector_FLP.c
        opus/silk/float/LTP_analysis_filter_FLP.c
        opus/silk/float/LTP_scale_ctrl_FLP.c
        opus/silk/float/find_LTP_FLP.c
        opus/silk/float/scale_vector_FLP.c
        opus/silk/float/regularize_correlations_FLP.c
        opus/silk/float/corrMatrix_FLP.c
        opus/silk/float/noise_shape_analysis_FLP.c
        opus/silk/float/bwexpander_FLP.c
        opus/silk/float/LPC_inv_pred_gain_FLP.c
        opus/silk/float/autocorrelation_FLP.c
        opus/silk/float/warped_autocorrelation_FLP.c
        opus/silk/float/apply_sine_window_FLP.c
        opus/silk/float/find_pitch_lags_FLP.c
        opus/silk/float/pitch_analysis_core_FLP.c
        opus/silk/pitch_est_tables.c
        opus/silk/float/sort_FLP.c
        opus/silk/resampler_down2.c
        opus/silk/resampler_down2_3.c
        opus/silk/float/k2a_FLP.c
        opus/silk/float/schur_FLP.c
        opus/silk/LP_variable_cutoff.c
        opus/silk/biquad_alt.c
        opus/silk/VAD.c
        opus/silk/sigm_Q15.c
        opus/silk/ana_filt_bank_1.c
        opus/silk/control_SNR.c
        opus/silk/stereo_encode_pred.c
        opus/silk/stereo_LR_to_MS.c
        opus/silk/stereo_quant_pred.c
        opus/silk/stereo_find_predictor.c
        opus/silk/inner_prod_aligned.c
        opus/silk/sum_sqr_shift.c
        opus/silk/HP_variable_cutoff.c
        opus/silk/control_codec.c
        opus/silk/tables_NLSF_CB_NB_MB.c
        opus/silk/tables_NLSF_CB_WB.c
        opus/silk/control_audio_bandwidth.c
        opus/silk/init_encoder.c
        opus/silk/check_control_input.c
        opus/src/analysis.c
        opus/src/repacketizer.c
        opus/src/opus.c
        opus/src/opus_decoder.c
        opus/celt/celt_decoder.c
        opus/silk/dec_API.c
        opus/silk/stereo_MS_to_LR.c
        opus/silk/decode_frame.c
        opus/silk/PLC.c
        opus/silk/bwexpander.c
        opus/silk/CNG.c
        opus/silk/decode_core.c
        opus/silk/decode_parameters.c
        opus/silk/decode_pitch.c
        opus/silk/decode_pulses.c
        opus/silk/decode_indices.c
        opus/silk/stereo_decode_pred.c
        opus/silk/decoder_set_fs.c
        opus/silk/init_decoder.c
        opus/src/mlp.c
        opus/src/mlp_data.c
        opus/silk/LPC_fit.c)

include_directories(opus/src opus/include opus/celt opus/silk opus/silk/float)

add_definitions(-DOPUS_BUILD -DSTDC_HEADERS -DVAR_ARRAYS)
set_target_properties(opus PROPERTIES PUBLIC_HEADER "opus/include/opus.h;opus/include/opus_custom.h;opus/include/opus_defines.h;opus/include/opus_multistream.h;opus/include/opus_types.h")

install(TARGETS opus
        RUNTIME DESTINATION bin
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        PUBLIC_HEADER DESTINATION include)

#find_library(log-lib log)
#
#target_link_libraries(opus ${log-lib})
