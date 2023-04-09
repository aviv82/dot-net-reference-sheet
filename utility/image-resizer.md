# image resizer

```c#
sing System.Drawing;
using System.Drawing.Imaging;
using System.Drawing.Drawing2D;
  namespace image_resizer.helpers
  {
    public static class ImageHelper
    {
        private const string DESTINATIONPATH = @"../../../thumbs/";

        private static int ImageAspectRatioCalculator(double sourceWidth, double sourceHeight, int desiredWidth)
        {
            double aspectRatio = sourceWidth / sourceHeight;

            int desiredHeight = (int)Math.Floor(desiredWidth / aspectRatio);

            return desiredHeight;
        }

      public static void ResizeImageV2(byte[] originalArray, string fileName, int desiredWidth)
        {
            MemoryStream originalStream = new MemoryStream(originalArray, 0, originalArray.Length);
            originalStream.Write(originalArray, 0, originalArray.Length);

            Image originalImage = Image.FromStream(originalStream);

            originalStream.Close();
            Bitmap bitmap = new Bitmap(originalImage);

            double sourceWidth = originalImage.Width;
            double sourceHeight = originalImage.Height;

           int desiredHeight = ImageAspectRatioCalculator(sourceWidth, sourceHeight, desiredWidth);

            Bitmap bitmapToReturn = new Bitmap(desiredWidth, desiredHeight);

            Graphics g = Graphics.FromImage(bitmapToReturn);

            g.CompositingMode = CompositingMode.SourceCopy;
            g.InterpolationMode = InterpolationMode.HighQualityBicubic;
            g.DrawImage(originalImage, 0, 0, desiredWidth, desiredHeight);
            g.Dispose();

            bitmapToReturn.Save(DESTINATIONPATH + fileName, ImageFormat.Jpeg);

        }
    }
  }
```
