heif_ context* ctx = heif_ context_ alloc();
heif_ context_ read_ _from_ file(ctx, input_ filename, nullptr);
// get a handle to the primary image
heif_ image_ handle* handle;
heif_ context_ get_ pr imary_ _image_ handle(ctx， &handle);
// decode the image and convert colorspace to RGB，saved as 24bit interleaved
heif_ image* img;
heif_ decode_ image(handle, &img, heif_ colorspace_ RGB, heif_ _chroma_ interleaved_ _RGB, nullptr);
int stride;
const uint8_ _t* data = heif_ image_ get_ plane_ readonly(img, heif_ channel_ interleaved, &stride) ;
process data as needed ...
// clean up resources
heif_ image_ release(img);
heif_ image_ handle_ release(handle);
heif_ context_ _free(ctx);
