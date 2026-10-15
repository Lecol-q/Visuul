
cmake_minimum_required(VERSION 3.22)

project(Visuul VERSION 1.0.0)

add_subdirectory(../JUCE JUCE)

juce_add_plugin(Visuul
        COMPANY_NAME "MyCompany"
        IS_SYNTH FALSE
        NEEDS_MIDI_INPUT FALSE
        NEEDS_MIDI_OUTPUT FALSE
        IS_MIDI_EFFECT FALSE
        EDITOR_WANTS_KEYBOARD_FOCUS FALSE
        COPY_PLUGIN_AFTER_BUILD FALSE
        PLUGIN_MANUFACTURER_CODE MyCo
        PLUGIN_CODE SpV1
        FORMATS Standalone VST3 AU
        PRODUCT_NAME "Visuul"
        NEEDS_CURL FALSE

)

juce_generate_juce_header(Visuul)

target_sources(Visuul
        PRIVATE
        Source/PluginProcessor.cpp
        Source/PluginEditor.cpp
)

target_compile_features(Visuul
        PRIVATE
        cxx_std_17
)

target_link_libraries(Visuul
        PRIVATE
        juce::juce_audio_utils
        PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags
)

target_compile_definitions(Visuul
        PUBLIC
        JUCE_VST3_CAN_REPLACE_VST2=0
)
