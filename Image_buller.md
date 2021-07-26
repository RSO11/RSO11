import java.awt.*;
import java.awt.image.BufferedImage; import java.io.File;
import java.io.IOException; import javax.imageio.ImageIO; import javax.swing.*;

public class Image_Buller extends JFrame{


public static void main(String[] args)
throws IOException, InterruptedException
{
String Select_image= JOptionPane.showInputDialog("Enter File"); Color color[];

File Selecting = new File(Select_image);


BufferedImage inputimage = ImageIO.read(Selecting); BufferedImage outputimage = new BufferedImage( inputimage.getWidth(), inputimage.getHeight(),
BufferedImage.TYPE_INT_RGB); JOptionPane.showMessageDialog(null, "Please Wait	");

int i = 0;
int maximum = 400, radius = 10; int a1 = 0,
r1 = 0,
g1 = 0,
b1 = 0;
color = new Color[maximum];


int x = 1, y = 1, x1, y1, ex = 5, d = 0;


for
 (x = radius; x < inputimage.getHeight() - radius; x++) {
for (y = radius; y < inputimage.getWidth() - radius; y++) { for (x1 = x - radius; x1 < x + radius; x1++) {
for (y1 = y - radius; y1 < y + radius; y1++) { color[i++] = new Color(
inputimage.getRGB(y1, x1));
}
}
i = 0;
for (d = 0; d < maximum; d++) { a1 = a1 + color[d].getAlpha();
}


a1 = a1 / (maximum);
for (d = 0; d < maximum; d++) { r1 = r1 + color[d].getRed();
}


r1 = r1 / (maximum);
for (d = 0; d < maximum; d++) { g1 = g1 + color[d].getGreen();
}


g1 = g1 / (maximum);
for (d = 0; d < maximum; d++) { b1 = b1 + color[d].getBlue();
}


b1 = b1 / (maximum);
int sum1 = (a1 << 24) + (r1 << 16)
+ (g1 << 8) + b1;
outputimage.setRGB(y, x, (int)(sum1));
}
}


ImageIO.write(
outputimage, "jpg",
new File("E:/Bullerd_Image2.jpg")); JOptionPane.showMessageDialog(null,"Blurred Succss Thank You...!");

}
}
