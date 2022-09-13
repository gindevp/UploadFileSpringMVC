# UploadFileSpringMVCThymeleaf

    upload_file.properties là file cấu hình tĩnh (có sẵn) trong pakage resources

    @PropertySource("classpath:upload_file.properties") viết ở trên đầu ngoại class
    @Value("${file-upload}") dùng để gán đường dẫn có sẵn cho biến
    private String fileUpload; // = chuỗi "file-upload"


 //Ẩn links dẫn tới file ảnh
 
    @Override
    public void addResourceHandlers(ResourceHandlerRegistry registry) {
        registry.addResourceHandler("/image/**")
                .addResourceLocations("file:" + fileUpload);

    }

    @Bean(name = "multipartResolver")
    public CommonsMultipartResolver getResolver() throws IOException {
        CommonsMultipartResolver resolver = new CommonsMultipartResolver();
        //max la 52mb
        resolver.setMaxUploadSizePerFile(52428800);
        return resolver;
    }
