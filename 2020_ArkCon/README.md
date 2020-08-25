# ArkCon 2020 Teaser

ArkCon 2020 was canceled due to the COVID-19 global pandemic, and the only challenge released was a teaser:

> Have you missed ArkCon? Check out our mini teaser! Just making sure you’re still in shape... 
> 
> http://0x7e4-challenge.com/

Visiting the website, we get a simple text box with the label "Answer". If we check the sources, we find the following script:

```javascript
    const memory = new WebAssembly.Memory({ initial: 256, maximum: 256 });
    const importObj = {
        env: {
            abortStackOverflow: () => { throw new Error('overflow'); },
            table: new WebAssembly.Table({ initial: 0, maximum: 0, element: 'anyfunc' }),
            __table_base: 0,
            memory: memory,
            __memory_base: 1024,
            STACKTOP: 0,
            STACK_MAX: memory.buffer.byteLength,
        }
    };

    document.getElementById('form').addEventListener('submit', function(e) {
        e.preventDefault();
        (async () => {
        const buff = new Uint8Array([
            187, 218, 200, 214, 186, 187, 187, 187, 186, 137, 185, 219, 186, 196, 187, 219, 146, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 196, 186, 196, 185, 216, 190, 184, 222, 213, 205, 169, 218, 217, 212, 201, 207, 232, 207, 218, 216, 208, 244, 205, 222, 201, 221, 215, 212, 204, 187, 187, 184, 222, 213, 205, 182, 228, 228, 214, 222, 214, 212, 201, 194, 228, 217, 218, 200, 222, 184, 196, 187, 184, 222, 213, 205, 183, 228, 228, 207, 218, 217, 215, 222, 228, 217, 218, 200, 222, 184, 196, 187, 184, 222, 213, 205, 189, 214, 222, 214, 212, 201, 194, 185, 186, 59, 185, 59, 185, 184, 222, 213, 205, 190, 207, 218, 217, 215, 222, 186, 203, 186, 187, 187, 184, 185, 186, 186, 189, 172, 184, 196, 186, 250, 27, 171, 176, 196, 186, 250, 27, 43, 123, 185, 176, 198, 186, 248, 187, 187, 187, 187, 176, 188, 179, 186, 191, 228, 205, 222, 201, 187, 186, 177, 71, 152, 186, 66, 152, 186, 115, 184, 196, 152, 185, 154, 84, 184, 152, 185, 250, 11, 186, 209, 159, 185, 152, 185, 152, 184, 245, 191, 251, 250, 11, 186, 171, 187, 176, 155, 187, 154, 27, 185, 155, 186, 154, 26, 185, 155, 185, 154, 23, 185, 155, 184, 154, 12, 185, 155, 191, 154, 121, 185, 155, 190, 154, 127, 185, 155, 189, 154, 126, 185, 155, 188, 154, 125, 185, 155, 179, 154, 124, 185, 155, 178, 154, 115, 185, 155, 177, 154, 25, 185, 155, 176, 154, 24, 185, 155, 183, 154, 31, 185, 155, 182, 154, 30, 185, 155, 181, 154, 29, 185, 155, 180, 154, 28, 185, 155, 171, 154, 19, 185, 155, 170, 154, 18, 185, 155, 169, 154, 17, 185, 155, 168, 154, 16, 185, 155, 175, 154, 22, 185, 155, 174, 154, 21, 185, 155, 173, 154, 20, 185, 155, 172, 154, 11, 185, 155, 163, 154, 10, 185, 155, 162, 154, 9, 185, 155, 161, 154, 8, 185, 155, 160, 154, 15, 185, 155, 167, 154, 14, 185, 155, 166, 154, 13, 185, 155, 165, 154, 3, 185, 155, 164, 154, 2, 185, 155, 155, 154, 1, 185, 155, 154, 154, 0, 185, 155, 153, 154, 7, 185, 155, 152, 154, 6, 185, 155, 159, 154, 5, 185, 155, 158, 154, 4, 185, 155, 157, 154, 123, 185, 155, 156, 154, 122, 185, 155, 147, 154, 120, 185, 250, 187, 154, 127, 184, 155, 27, 185, 154, 146, 155, 146, 250, 196, 200, 154, 73, 185, 155, 73, 185, 250, 107, 186, 202, 154, 117, 186, 155, 27, 185, 154, 145, 155, 145, 250, 20, 197, 202, 154, 116, 186, 155, 117, 186, 155, 116, 186, 201, 154, 32, 184, 155, 32, 184, 250, 3, 186, 208, 154, 126, 184, 185, 196, 155, 126, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 114, 185, 155, 127, 184, 154, 246, 155, 246, 155, 114, 185, 209, 154, 30, 186, 155, 30, 186, 154, 127, 184, 155, 26, 185, 154, 227, 155, 227, 250, 196, 200, 154, 56, 184, 155, 56, 184, 250, 41, 186, 202, 154, 49, 185, 155, 26, 185, 154, 216, 155, 216, 250, 86, 197, 202, 154, 52, 185, 155, 49, 185, 155, 52, 185, 201, 154, 7, 184, 155, 7, 184, 250, 93, 186, 208, 154, 92, 184, 185, 196, 155, 92, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 87, 185, 155, 127, 184, 154, 213, 155, 213, 155, 87, 185, 209, 154, 113, 186, 155, 113, 186, 154, 127, 184, 155, 23, 185, 154, 194, 155, 194, 250, 196, 200, 154, 34, 184, 155, 34, 184, 250, 95, 187, 202, 154, 107, 186, 155, 23, 185, 154, 63, 186, 155, 63, 186, 250, 32, 196, 202, 154, 110, 186, 155, 107, 186, 155, 110, 186, 201, 154, 36, 184, 155, 36, 184, 250, 171, 208, 154, 113, 184, 185, 196, 155, 113, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 116, 185, 155, 127, 184, 154, 52, 186, 155, 52, 186, 155, 116, 185, 209, 154, 22, 186, 155, 22, 186, 154, 127, 184, 155, 12, 185, 154, 33, 186, 155, 33, 186, 250, 196, 200, 154, 71, 185, 155, 71, 185, 250, 112, 186, 202, 154, 93, 186, 155, 12, 185, 154, 144, 155, 144, 250, 15, 197, 202, 154, 80, 186, 155, 93, 186, 155, 80, 186, 201, 154, 17, 184, 155, 17, 184, 250, 0, 186, 208, 154, 110, 184, 185, 196, 155, 110, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 97, 185, 155, 127, 184, 154, 141, 155, 141, 155, 97, 185, 209, 154, 3, 186, 155, 3, 186, 154, 127, 184, 155, 121, 185, 154, 250, 155, 250, 250, 196, 200, 154, 51, 184, 155, 51, 184, 250, 184, 202, 154, 71, 186, 155, 121, 185, 154, 253, 155, 253, 250, 199, 202, 154, 58, 185, 155, 71, 186, 155, 58, 185, 201, 154, 14, 184, 155, 14, 184, 250, 130, 208, 154, 91, 184, 185, 196, 155, 91, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 94, 185, 155, 127, 184, 154, 252, 155, 252, 155, 94, 185, 209, 154, 121, 186, 155, 121, 186, 154, 127, 184, 155, 127, 185, 154, 243, 155, 243, 250, 196, 200, 154, 43, 184, 155, 43, 184, 250, 134, 202, 154, 48, 185, 155, 127, 185, 154, 242, 155, 242, 250, 249, 202, 154, 55, 185, 155, 48, 185, 155, 55, 185, 201, 154, 2, 184, 155, 2, 184, 250, 169, 208, 154, 88, 184, 185, 196, 155, 88, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 92, 185, 155, 127, 184, 154, 241, 155, 241, 155, 92, 185, 209, 154, 120, 186, 155, 120, 186, 154, 127, 184, 155, 126, 185, 154, 240, 155, 240, 250, 196, 200, 154, 42, 184, 155, 42, 184, 250, 184, 202, 154, 54, 185, 155, 126, 185, 154, 247, 155, 247, 250, 199, 202, 154, 53, 185, 155, 54, 185, 155, 53, 185, 201, 154, 1, 184, 155, 1, 184, 250, 151, 208, 154, 95, 184, 185, 196, 155, 95, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 83, 185, 155, 127, 184, 154, 245, 155, 245, 155, 83, 185, 209, 154, 127, 186, 155, 127, 186, 154, 127, 184, 155, 125, 185, 154, 244, 155, 244, 250, 196, 200, 154, 41, 184, 155, 41, 184, 250, 29, 186, 202, 154, 43, 185, 155, 125, 185, 154, 235, 155, 235, 250, 98, 197, 202, 154, 42, 185, 155, 43, 185, 155, 42, 185, 201, 154, 0, 184, 155, 0, 184, 250, 117, 186, 208, 154, 94, 184, 185, 196, 155, 94, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 82, 185, 155, 127, 184, 154, 234, 155, 234, 155, 82, 185, 209, 154, 126, 186, 155, 126, 186, 154, 127, 184, 155, 124, 185, 154, 233, 155, 233, 250, 196, 200, 154, 40, 184, 155, 40, 184, 250, 145, 202, 154, 41, 185, 155, 124, 185, 154, 232, 155, 232, 250, 238, 202, 154, 40, 185, 155, 41, 185, 155, 40, 185, 201, 154, 6, 184, 155, 6, 184, 250, 162, 208, 154, 93, 184, 185, 196, 155, 93, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 81, 185, 155, 127, 184, 154, 239, 155, 239, 155, 81, 185, 209, 154, 125, 186, 155, 125, 186, 154, 127, 184, 155, 115, 185, 154, 238, 155, 238, 250, 196, 200, 154, 47, 184, 155, 47, 184, 250, 44, 186, 202, 154, 47, 185, 155, 115, 185, 154, 237, 155, 237, 250, 83, 197, 202, 154, 46, 185, 155, 47, 185, 155, 46, 185, 201, 154, 5, 184, 155, 5, 184, 250, 79, 186, 208, 154, 83, 184, 185, 196, 155, 83, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 80, 185, 155, 127, 184, 154, 236, 155, 236, 155, 80, 185, 209, 154, 124, 186, 155, 124, 186, 154, 127, 184, 155, 25, 185, 154, 226, 155, 226, 250, 196, 200, 154, 46, 184, 155, 46, 184, 250, 65, 186, 202, 154, 45, 185, 155, 25, 185, 154, 225, 155, 225, 250, 62, 197, 202, 154, 44, 185, 155, 45, 185, 155, 44, 185, 201, 154, 4, 184, 155, 4, 184, 250, 42, 186, 208, 154, 82, 184, 185, 196, 155, 82, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 86, 185, 155, 127, 184, 154, 224, 155, 224, 155, 86, 185, 209, 154, 115, 186, 155, 115, 186, 154, 127, 184, 155, 24, 185, 154, 231, 155, 231, 250, 196, 200, 154, 45, 184, 155, 45, 184, 250, 106, 186, 202, 154, 35, 185, 155, 24, 185, 154, 230, 155, 230, 250, 21, 197, 202, 154, 34, 185, 155, 35, 185, 155, 34, 185, 201, 154, 123, 184, 155, 123, 184, 250, 71, 186, 208, 154, 81, 184, 185, 196, 155, 81, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 85, 185, 155, 127, 184, 154, 229, 155, 229, 155, 85, 185, 209, 154, 114, 186, 155, 114, 186, 154, 127, 184, 155, 31, 185, 154, 228, 155, 228, 250, 196, 200, 154, 44, 184, 155, 44, 184, 250, 66, 186, 202, 154, 33, 185, 155, 31, 185, 154, 219, 155, 219, 250, 61, 197, 202, 154, 32, 185, 155, 33, 185, 155, 32, 185, 201, 154, 122, 184, 155, 122, 184, 250, 59, 186, 208, 154, 80, 184, 185, 196, 155, 80, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 84, 185, 155, 127, 184, 154, 218, 155, 218, 155, 84, 185, 209, 154, 112, 186, 155, 112, 186, 154, 127, 184, 155, 30, 185, 154, 217, 155, 217, 250, 196, 200, 154, 35, 184, 155, 35, 184, 250, 49, 186, 202, 154, 39, 185, 155, 30, 185, 154, 223, 155, 223, 250, 78, 197, 202, 154, 38, 185, 155, 39, 185, 155, 38, 185, 201, 154, 121, 184, 155, 121, 184, 250, 2, 186, 208, 154, 87, 184, 185, 196, 155, 87, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 75, 185, 155, 127, 184, 154, 222, 155, 222, 155, 75, 185, 209, 154, 119, 186, 155, 119, 186, 154, 127, 184, 155, 29, 185, 154, 221, 155, 221, 250, 196, 200, 154, 33, 184, 155, 33, 184, 250, 24, 186, 202, 154, 37, 185, 155, 29, 185, 154, 220, 155, 220, 250, 103, 197, 202, 154, 36, 185, 155, 37, 185, 155, 36, 185, 201, 154, 120, 184, 155, 120, 184, 250, 44, 186, 208, 154, 86, 184, 185, 196, 155, 86, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 74, 185, 155, 127, 184, 154, 211, 155, 211, 155, 74, 185, 209, 154, 118, 186, 155, 118, 186, 154, 127, 184, 155, 28, 185, 154, 210, 155, 210, 250, 196, 200, 154, 72, 185, 155, 72, 185, 250, 43, 186, 202, 154, 106, 186, 155, 28, 185, 154, 209, 155, 209, 250, 84, 197, 202, 154, 105, 186, 155, 106, 186, 155, 105, 186, 201, 154, 39, 184, 155, 39, 184, 250, 67, 186, 208, 154, 125, 184, 185, 196, 155, 125, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 113, 185, 155, 127, 184, 154, 208, 155, 208, 155, 113, 185, 209, 154, 29, 186, 155, 29, 186, 154, 127, 184, 155, 19, 185, 154, 215, 155, 215, 250, 196, 200, 154, 79, 185, 155, 79, 185, 250, 45, 186, 202, 154, 104, 186, 155, 19, 185, 154, 214, 155, 214, 250, 82, 197, 202, 154, 111, 186, 155, 104, 186, 155, 111, 186, 201, 154, 38, 184, 155, 38, 184, 250, 0, 186, 208, 154, 124, 184, 185, 196, 155, 124, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 112, 185, 155, 127, 184, 154, 212, 155, 212, 155, 112, 185, 209, 154, 28, 186, 155, 28, 186, 154, 127, 184, 155, 18, 185, 154, 203, 155, 203, 250, 196, 200, 154, 78, 185, 155, 78, 185, 250, 121, 187, 202, 154, 109, 186, 155, 18, 185, 154, 202, 155, 202, 250, 6, 196, 202, 154, 108, 186, 155, 109, 186, 155, 108, 186, 201, 154, 37, 184, 155, 37, 184, 250, 79, 187, 208, 154, 115, 184, 185, 196, 155, 115, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 119, 185, 155, 127, 184, 154, 201, 155, 201, 155, 119, 185, 209, 154, 19, 186, 155, 19, 186, 154, 127, 184, 155, 17, 185, 154, 200, 155, 200, 250, 196, 200, 154, 77, 185, 155, 77, 185, 250, 79, 186, 202, 154, 99, 186, 155, 17, 185, 154, 207, 155, 207, 250, 48, 197, 202, 154, 98, 186, 155, 99, 186, 155, 98, 186, 201, 154, 27, 184, 155, 27, 184, 250, 126, 186, 208, 154, 114, 184, 185, 196, 155, 114, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 118, 185, 155, 127, 184, 154, 206, 155, 206, 155, 118, 185, 209, 154, 18, 186, 155, 18, 186, 154, 127, 184, 155, 16, 185, 154, 205, 155, 205, 250, 196, 200, 154, 76, 185, 155, 76, 185, 250, 129, 202, 154, 97, 186, 155, 16, 185, 154, 204, 155, 204, 250, 254, 202, 154, 96, 186, 155, 97, 186, 155, 96, 186, 201, 154, 26, 184, 155, 26, 184, 250, 108, 187, 208, 154, 112, 184, 185, 196, 155, 112, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 117, 185, 155, 127, 184, 154, 195, 155, 195, 155, 117, 185, 209, 154, 17, 186, 155, 17, 186, 154, 127, 184, 155, 22, 185, 154, 193, 155, 193, 250, 196, 200, 154, 67, 185, 155, 67, 185, 250, 174, 202, 154, 103, 186, 155, 22, 185, 154, 192, 155, 192, 250, 209, 202, 154, 102, 186, 155, 103, 186, 155, 102, 186, 201, 154, 25, 184, 155, 25, 184, 250, 67, 187, 208, 154, 119, 184, 185, 196, 155, 119, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 107, 185, 155, 127, 184, 154, 199, 155, 199, 155, 107, 185, 209, 154, 16, 186, 155, 16, 186, 154, 127, 184, 155, 21, 185, 154, 198, 155, 198, 250, 196, 200, 154, 66, 185, 155, 66, 185, 250, 45, 186, 202, 154, 101, 186, 155, 21, 185, 154, 197, 155, 197, 250, 82, 197, 202, 154, 100, 186, 155, 101, 186, 155, 100, 186, 201, 154, 24, 184, 155, 24, 184, 250, 30, 186, 208, 154, 118, 184, 185, 196, 155, 118, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 106, 185, 155, 127, 184, 154, 196, 155, 196, 155, 106, 185, 209, 154, 23, 186, 155, 23, 186, 154, 127, 184, 155, 20, 185, 154, 59, 186, 155, 59, 186, 250, 196, 200, 154, 65, 185, 155, 65, 185, 250, 104, 186, 202, 154, 91, 186, 155, 20, 185, 154, 58, 186, 155, 58, 186, 250, 23, 197, 202, 154, 90, 186, 155, 91, 186, 155, 90, 186, 201, 154, 31, 184, 155, 31, 184, 250, 69, 186, 208, 154, 117, 184, 185, 196, 155, 117, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 105, 185, 155, 127, 184, 154, 57, 186, 155, 57, 186, 155, 105, 185, 209, 154, 21, 186, 155, 21, 186, 154, 127, 184, 155, 11, 185, 154, 56, 186, 155, 56, 186, 250, 196, 200, 154, 64, 185, 155, 64, 185, 250, 94, 186, 202, 154, 89, 186, 155, 11, 185, 154, 62, 186, 155, 62, 186, 250, 33, 197, 202, 154, 88, 186, 155, 89, 186, 155, 88, 186, 201, 154, 30, 184, 155, 30, 184, 250, 107, 186, 208, 154, 116, 184, 185, 196, 155, 116, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 104, 185, 155, 127, 184, 154, 61, 186, 155, 61, 186, 155, 104, 185, 209, 154, 20, 186, 155, 20, 186, 154, 127, 184, 155, 10, 185, 154, 60, 186, 155, 60, 186, 250, 196, 200, 154, 70, 185, 155, 70, 185, 250, 0, 186, 202, 154, 95, 186, 155, 10, 185, 154, 51, 186, 155, 51, 186, 250, 127, 197, 202, 154, 94, 186, 155, 95, 186, 155, 94, 186, 201, 154, 29, 184, 155, 29, 184, 250, 48, 186, 208, 154, 107, 184, 185, 196, 155, 107, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 111, 185, 155, 127, 184, 154, 50, 186, 155, 50, 186, 155, 111, 185, 209, 154, 11, 186, 155, 11, 186, 154, 127, 184, 155, 9, 185, 154, 49, 186, 155, 49, 186, 250, 196, 200, 154, 69, 185, 155, 69, 185, 250, 24, 186, 202, 154, 92, 186, 155, 9, 185, 154, 48, 186, 155, 48, 186, 250, 103, 197, 202, 154, 83, 186, 155, 92, 186, 155, 83, 186, 201, 154, 28, 184, 155, 28, 184, 250, 117, 186, 208, 154, 106, 184, 185, 196, 155, 106, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 110, 185, 155, 127, 184, 154, 55, 186, 155, 55, 186, 155, 110, 185, 209, 154, 10, 186, 155, 10, 186, 154, 127, 184, 155, 8, 185, 154, 54, 186, 155, 54, 186, 250, 196, 200, 154, 68, 185, 155, 68, 185, 250, 80, 187, 202, 154, 82, 186, 155, 8, 185, 154, 53, 186, 155, 53, 186, 250, 47, 196, 202, 154, 81, 186, 155, 82, 186, 155, 81, 186, 201, 154, 19, 184, 155, 19, 184, 250, 99, 187, 208, 154, 105, 184, 185, 196, 155, 105, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 109, 185, 155, 127, 184, 154, 43, 186, 155, 43, 186, 155, 109, 185, 209, 154, 9, 186, 155, 9, 186, 154, 127, 184, 155, 15, 185, 154, 42, 186, 155, 42, 186, 250, 196, 200, 154, 59, 184, 155, 59, 184, 250, 21, 186, 202, 154, 87, 186, 155, 15, 185, 154, 41, 186, 155, 41, 186, 250, 106, 197, 202, 154, 86, 186, 155, 87, 186, 155, 86, 186, 201, 154, 18, 184, 155, 18, 184, 250, 56, 186, 208, 154, 104, 184, 185, 196, 155, 104, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 108, 185, 155, 127, 184, 154, 40, 186, 155, 40, 186, 155, 108, 185, 209, 154, 8, 186, 155, 8, 186, 154, 127, 184, 155, 14, 185, 154, 47, 186, 155, 47, 186, 250, 196, 200, 154, 58, 184, 155, 58, 184, 250, 81, 187, 202, 154, 85, 186, 155, 14, 185, 154, 46, 186, 155, 46, 186, 250, 46, 196, 202, 154, 84, 186, 155, 85, 186, 155, 84, 186, 201, 154, 16, 184, 155, 16, 184, 250, 178, 208, 154, 111, 184, 185, 196, 155, 111, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 99, 185, 155, 127, 184, 154, 45, 186, 155, 45, 186, 155, 99, 185, 209, 154, 15, 186, 155, 15, 186, 154, 127, 184, 155, 13, 185, 154, 44, 186, 155, 44, 186, 250, 196, 200, 154, 57, 184, 155, 57, 184, 250, 153, 202, 154, 75, 186, 155, 13, 185, 154, 35, 186, 155, 35, 186, 250, 230, 202, 154, 74, 186, 155, 75, 186, 155, 74, 186, 201, 154, 23, 184, 155, 23, 184, 250, 169, 208, 154, 109, 184, 185, 196, 155, 109, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 98, 185, 155, 127, 184, 154, 34, 186, 155, 34, 186, 155, 98, 185, 209, 154, 14, 186, 155, 14, 186, 154, 127, 184, 155, 3, 185, 154, 32, 186, 155, 32, 186, 250, 196, 200, 154, 63, 184, 155, 63, 184, 250, 1, 186, 202, 154, 73, 186, 155, 3, 185, 154, 39, 186, 155, 39, 186, 250, 126, 197, 202, 154, 72, 186, 155, 73, 186, 155, 72, 186, 201, 154, 22, 184, 155, 22, 184, 250, 49, 186, 208, 154, 108, 184, 185, 196, 155, 108, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 96, 185, 155, 127, 184, 154, 38, 186, 155, 38, 186, 155, 96, 185, 209, 154, 13, 186, 155, 13, 186, 154, 127, 184, 155, 2, 185, 154, 37, 186, 155, 37, 186, 250, 196, 200, 154, 62, 184, 155, 62, 184, 250, 90, 186, 202, 154, 79, 186, 155, 2, 185, 154, 36, 186, 155, 36, 186, 250, 37, 197, 202, 154, 78, 186, 155, 79, 186, 155, 78, 186, 201, 154, 21, 184, 155, 21, 184, 250, 54, 186, 208, 154, 99, 184, 185, 196, 155, 99, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 103, 185, 155, 127, 184, 154, 27, 186, 155, 27, 186, 155, 103, 185, 209, 154, 12, 186, 155, 12, 186, 154, 127, 184, 155, 1, 185, 154, 26, 186, 155, 26, 186, 250, 196, 200, 154, 61, 184, 155, 61, 184, 250, 179, 202, 154, 77, 186, 155, 1, 185, 154, 25, 186, 155, 25, 186, 250, 204, 202, 154, 76, 186, 155, 77, 186, 155, 76, 186, 201, 154, 20, 184, 155, 20, 184, 250, 158, 208, 154, 98, 184, 185, 196, 155, 98, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 102, 185, 155, 127, 184, 154, 24, 186, 155, 24, 186, 155, 102, 185, 209, 154, 2, 186, 155, 2, 186, 154, 127, 184, 155, 0, 185, 154, 31, 186, 155, 31, 186, 250, 196, 200, 154, 60, 184, 155, 60, 184, 250, 183, 202, 154, 67, 186, 155, 0, 185, 154, 151, 155, 151, 250, 200, 202, 154, 66, 186, 155, 67, 186, 155, 66, 186, 201, 154, 11, 184, 155, 11, 184, 250, 130, 208, 154, 97, 184, 185, 196, 155, 97, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 101, 185, 155, 127, 184, 154, 150, 155, 150, 155, 101, 185, 209, 154, 1, 186, 155, 1, 186, 154, 127, 184, 155, 7, 185, 154, 149, 155, 149, 250, 196, 200, 154, 50, 184, 155, 50, 184, 250, 133, 202, 154, 65, 186, 155, 7, 185, 154, 148, 155, 148, 250, 250, 202, 154, 64, 186, 155, 65, 186, 155, 64, 186, 201, 154, 10, 184, 155, 10, 184, 250, 114, 187, 208, 154, 96, 184, 185, 196, 155, 96, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 100, 185, 155, 127, 184, 154, 139, 155, 139, 155, 100, 185, 209, 154, 0, 186, 155, 0, 186, 154, 127, 184, 155, 6, 185, 154, 138, 155, 138, 250, 196, 200, 154, 49, 184, 155, 49, 184, 250, 95, 186, 202, 154, 70, 186, 155, 6, 185, 154, 137, 155, 137, 250, 32, 197, 202, 154, 69, 186, 155, 70, 186, 155, 69, 186, 201, 154, 9, 184, 155, 9, 184, 250, 107, 186, 208, 154, 103, 184, 185, 196, 155, 103, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 91, 185, 155, 127, 184, 154, 136, 155, 136, 155, 91, 185, 209, 154, 7, 186, 155, 7, 186, 154, 127, 184, 155, 5, 185, 154, 143, 155, 143, 250, 196, 200, 154, 48, 184, 155, 48, 184, 250, 110, 187, 202, 154, 68, 186, 155, 5, 185, 154, 142, 155, 142, 250, 17, 196, 202, 154, 59, 185, 155, 68, 186, 155, 59, 185, 201, 154, 8, 184, 155, 8, 184, 250, 88, 187, 208, 154, 102, 184, 185, 196, 155, 102, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 90, 185, 155, 127, 184, 154, 140, 155, 140, 155, 90, 185, 209, 154, 6, 186, 155, 6, 186, 154, 127, 184, 155, 4, 185, 154, 131, 155, 131, 250, 196, 200, 154, 55, 184, 155, 55, 184, 250, 85, 187, 202, 154, 57, 185, 155, 4, 185, 154, 130, 155, 130, 250, 42, 196, 202, 154, 56, 185, 155, 57, 185, 155, 56, 185, 201, 154, 15, 184, 155, 15, 184, 250, 123, 187, 208, 154, 101, 184, 185, 196, 155, 101, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 89, 185, 155, 127, 184, 154, 129, 155, 129, 155, 89, 185, 209, 154, 5, 186, 155, 5, 186, 154, 127, 184, 155, 123, 185, 154, 128, 155, 128, 250, 196, 200, 154, 54, 184, 155, 54, 184, 250, 116, 187, 202, 154, 63, 185, 155, 123, 185, 154, 135, 155, 135, 250, 11, 196, 202, 154, 62, 185, 155, 63, 185, 155, 62, 185, 201, 154, 13, 184, 155, 13, 184, 250, 140, 208, 154, 100, 184, 185, 196, 155, 100, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 88, 185, 155, 127, 184, 154, 134, 155, 134, 155, 88, 185, 209, 154, 4, 186, 155, 4, 186, 154, 127, 184, 155, 122, 185, 154, 133, 155, 133, 250, 196, 200, 154, 53, 184, 155, 53, 184, 250, 88, 186, 202, 154, 61, 185, 155, 122, 185, 154, 132, 155, 132, 250, 39, 197, 202, 154, 60, 185, 155, 61, 185, 155, 60, 185, 201, 154, 12, 184, 155, 12, 184, 250, 33, 186, 208, 154, 90, 184, 185, 196, 155, 90, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 95, 185, 155, 127, 184, 154, 251, 155, 251, 155, 95, 185, 209, 154, 123, 186, 155, 123, 186, 154, 127, 184, 155, 120, 185, 154, 249, 155, 249, 250, 196, 200, 154, 52, 184, 155, 52, 184, 250, 181, 202, 154, 51, 185, 155, 120, 185, 154, 248, 155, 248, 250, 202, 202, 154, 50, 185, 155, 51, 185, 155, 50, 185, 201, 154, 3, 184, 155, 3, 184, 250, 79, 187, 208, 154, 89, 184, 185, 196, 155, 89, 184, 154, 75, 184, 250, 187, 155, 75, 184, 208, 155, 75, 184, 155, 75, 184, 250, 187, 243, 160, 176, 154, 93, 185, 155, 127, 184, 154, 255, 155, 255, 155, 93, 185, 209, 154, 122, 186, 155, 122, 186, 154, 127, 184, 155, 127, 184, 154, 254, 155, 84, 184, 159, 185, 155, 254, 180, 176]);debugger

        buff.forEach(function(b, i) {this[i]  = b ^ 0xbb}, buff);debugger

        const { instance } = await WebAssembly.instantiate(buff, importObj);debugger;const encoder = new TextEncoder();
        const answer = document.getElementById('answer').value;debugger;window['console']['log'] = instance.exports._ver;
        const a = encoder.encode(answer);debugger;var result = console.log(...a);

        if (result == 0) {
                result = "😸";
        } else {
                result = "😾";
        }  
        document.querySelector('main').textContent = ` ${ result }`;
        })();
    });
```

What do we have here?

We have an array of bytes named `buff`, which when XORed with `0xbb` gives a WebAssembly program. The program exports a function under `instance.exports._ver;`, which is used to replace the default `console.log` function. 

In addition, the user input we provide is encoded as ASCII and sent to this exported function. If the result of the function is `0`, the answer is accepted. Otherwise, the answer is rejected.

Let's run the function with some random input to see what it returns:

```
console.log("test")
2031
```

That's obviously not zero. In order to provide the correct input we'll need to analyze the program. We first have to decode it though.

```python
>>> arr = [187, 218, 200, 214, 186, ..., 155, 254, 180, 176]
>>> with open("program.wasm", "wb") as f:
...     f.write(bytes([x ^ 0xbb for x in arr]))
...
4807
```

Let's take a look at the output:

```console
root@kali:/media/sf_CTFs/arkcon/teaser# xxd -g 1 program.wasm | head
00000000: 00 61 73 6d 01 00 00 00 01 32 02 60 01 7f 00 60  .asm.....2.`...`
00000010: 29 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f  )...............
00000020: 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f  ................
00000030: 7f 7f 7f 7f 7f 7f 7f 7f 7f 7f 01 7f 02 63 05 03  .............c..
00000040: 65 6e 76 12 61 62 6f 72 74 53 74 61 63 6b 4f 76  env.abortStackOv
00000050: 65 72 66 6c 6f 77 00 00 03 65 6e 76 0d 5f 5f 6d  erflow...env.__m
00000060: 65 6d 6f 72 79 5f 62 61 73 65 03 7f 00 03 65 6e  emory_base....en
00000070: 76 0c 5f 5f 74 61 62 6c 65 5f 62 61 73 65 03 7f  v.__table_base..
00000080: 00 03 65 6e 76 06 6d 65 6d 6f 72 79 02 01 80 02  ..env.memory....
00000090: 80 02 03 65 6e 76 05 74 61 62 6c 65 01 70 01 00  ...env.table.p..
```

This certainly looks like WebAssembly. 

There are tools such as [wasm2wat](https://github.com/WebAssembly/wabt) to turn this into WebAssembly text format:

```console
root@kali:/media/sf_CTFs/arkcon/teaser#  ~/utils/wabt/build/wasm2wat program.wasm | head
(module
  (type (;0;) (func (param i32)))
  (type (;1;) (func (param i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32) (result i32)))
  (import "env" "abortStackOverflow" (func (;0;) (type 0)))
  (import "env" "__memory_base" (global (;0;) i32))
  (import "env" "__table_base" (global (;1;) i32))
  (import "env" "memory" (memory (;0;) 256 256))
  (import "env" "table" (table (;0;) 0 0 funcref))
  (func (;1;) (type 1) (param i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32) (result i32)
    (local i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32 i32)
```

However it's much more convenient to use a WebAssembly to C decompiler such as [wasmdec](https://github.com/wwwg/wasmdec) to get something that resembles C output:
```console
root@kali:/media/sf_CTFs/arkcon/teaser# wasmdec -o program.c program.wasm
```

This gives us some cryptic definitions and utility functions at the beginning of the file, followed by some WASM globals:

```c
extern int gimport$1; /* import */
extern int gimport$2; /* import */
int global$0 = 2080;
int global$1 = 5244960;
float global$2 = 0.000000;

extern void ffimport$0(int local0); /* import */
```

Finally, we get a function implementation.

Here's the prototype:
```c
int f0(int local0, int local1, int local2, int local3, int local4, int local5, int local6, int local7, int local8, int local9, int local10, int local11, int local12, int local13, int local14, int local15, int local16, int local17, int local18, int local19, int local20, int local21, int local22, int local23, int local24, int local25, int local26, int local27, int local28, int local29, int local30, int local31, int local32, int local33, int local34, int local35, int local36, int local37, int local38, int local39, int local40)
```

Then come some assignments, followed by lots of logic such as:
```c
	local452 = 0;
	local41 = local288;
	local370 = local41 ^ -1;
	local206 = local370 & 208;
	local42 = local288;
	local207 = local42 & -209;
	local411 = local206 | local207;
	local453 = local411 - 184;
	local329 = 	label$2:
	local496 = local453;
(local496 < 0) ? (0 - local496) : (local496);
;
	local77 = local452;
	local165 = local77 + local329;
	local452 = local165;
	local88 = local289;
	local387 = local88 ^ -1;
	local266 = local387 & 146;
	local99 = local289;
	local271 = local99 & -147;
	local444 = local266 | local271;
	local487 = local444 - 230;
	local364 = 	label$3:
	local496 = local487;
(local496 < 0) ? (0 - local496) : (local496);
;

// ...

	local64 = local452;
	local192 = local64 + local356;
	local452 = local192;
	local66 = local323;
	local399 = local66 ^ -1;
	local264 = local399 & 14;
	local67 = local323;
	local265 = local67 & -15;
	local440 = local264 | local265;
	local482 = local440 - 116;
	local358 = 	label$42:
	local496 = local482;
(local496 < 0) ? (0 - local496) : (local496);
;
```

At last, a value is returned:
```c
	local68 = local452;
	local193 = local68 + local358;
	local452 = local193;
	local69 = local452;
	global$0 = local495;
	return local69;
```

The full program can be found under `program.c`.

This looks like a classic task for Z3, we just need to translate the C code into Python. It's mostly trivial, but we do have some weird snippets such as:
```c
local358 = 	label$42:
local496 = local482;
(local496 < 0) ? (0 - local496) : (local496);
;
```

To translate them, we just need to realize that they are simply trying to implement the `abs()` function, so we can define:

```python
def abs(x):
    return If(x < 0, 0 - x, x)
```

And translate the above snippet to:
```python
local358 = 	abs(local482)
```

So, our script becomes:
```python
from z3 import *

def abs(x):
    return If(x < 0, 0 - x, x)

s = Solver()

KEY_LEN = 41 # Based on prototype of f0()

key = [BitVec("{}".format(i), 32) for i in range(KEY_LEN)]

# Indicate that key is composed of printable text only
for i in range(KEY_LEN):
    s.add(key[i] >= ord('!'))
    s.add(key[i] <= ord('~'))

local288 = key[0]
local289 = key[1]
# ...
local323 = key[40]

local452 = 0
local41 = local288
local370 = local41 ^ -1
local206 = local370 & 208
local42 = local288
local207 = local42 & -209
local411 = local206 | local207
local453 = local411 - 184
local329 = abs(local453)

local77 = local452
local165 = local77 + local329
local452 = local165
local88 = local289
local387 = local88 ^ -1
local266 = local387 & 146
local99 = local289
local271 = local99 & -147
local444 = local266 | local271
local487 = local444 - 230
local364 = 	abs(local487)

# ...

local64 = local452
local192 = local64 + local356
local452 = local192
local66 = local323
local399 = local66 ^ -1
local264 = local399 & 14
local67 = local323
local265 = local67 & -15
local440 = local264 | local265
local482 = local440 - 116
local358 = 	abs(local482)

local68 = local452
local193 = local68 + local358
local452 = local193
local69 = local452
# Not needed: global$0 = local495

# We want the return value to be 0
s.add(local69 == 0)

if s.check() == sat:
    model = s.model()
    res = ""
    for i in range(KEY_LEN):
        res += chr(model[key[i]].as_long())
    print(res)
```

The full program is attached as `solve.py`.

We run it and get:
```console
root@kali:/media/sf_CTFs/arkcon/teaser# python3 solve.py
http://h3ck-y34h-61mm3-50m3-c00l-5w46.xyz
```

The website contains the following message:
```
Yay. Hi Cracker 
You are the first one to solve the challenge!
Mmm.. Just joking.. Don't tell me you fell for that.
Unfortunately, ArkCon 2020 is cancelled due to the global pandemic.
It's important for us to see you IRL and not just behind the keyboard, so we decided to cancel this year's event and focus our efforts to make ArkCon 2021 the best ArkCon yet.
We already started working closely with our review board and international partners to create an engaging, enriching and challenging 2021 event.
Want to claim your trophy and get ArkCon updates before everyone?
Shoot us an email to ArkCon[at]CyberArk.com with your name and your t-shirt size.
Stay safe,
The ArkCon Team
```

See you next year.