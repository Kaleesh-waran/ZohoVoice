# Uncomment the next line to define a global platform for your project
platform :ios, '13.0'

source 'https://github.com/CocoaPods/Specs.git'
source 'https://git.csez.zohocorpin.com/zoho/zohopodspecs.git'
source 'https://git.csez.zohocorpin.com/vtouchzoho/vtouchpodspecs.git'
source 'https://git.csez.zohocorpin.com/zohonativecharts/podspecs.git' 

target 'ZVoice' do

  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

pod 'ZCharts','0.1.17'
pod 'Fastis', '~> 2.0'
pod 'SSOKit','2.0.13'
pod 'libPhoneNumber-iOS', '~> 0.8'
pod 'Cosmos', '~> 23.0'

end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.name == 'SSOKit-SSOKitBundle'
      target.build_configurations.each do |config|
        config.build_settings.delete('CODE_SIGNING_ALLOWED')
        config.build_settings.delete('CODE_SIGNING_REQUIRED')
        config.build_settings['CODE_SIGN_IDENTITY'] = ''
      end
    end
    if target.name == 'SSOKit'
        target.build_configurations.each do |config|
          if config.name == "InHouse - Local Zoho" || config.name == "Debug - Local Zoho"
            config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] = "$(inherited) SSO_LOCAL_MDM"
            end
        end
    end
  end
  installer.generated_projects.each do |project|
    project.targets.each do |target|
      target.build_configurations.each do |config|
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '13.0'
      end
    end
  end
end

