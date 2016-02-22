#include "video.h"

#define FG_GREEN 2
#define BG_BLACK 0

#define FB_COMMAND_PORT  0x3d4
#define FB_DATA_PORT     0x3d5
#define FB_HIGH_BYTE_CMD 14
#define FB_LOW_BYTE_CMD  15

void putchar(unsigned int i, char c, unsigned char fg, unsigned char bg);
void putstring(unsigned int i, char c[], unsigned char fg, unsigned char bg);
void curpos(unsigned short pos);
int strlen(char c[]);

void clear();

int kmain()
{
   putchar(0, 'A', FG_GREEN, BG_BLACK);
   clear();
   char s[] = "hello!\0";
   putstring(0, s, FG_GREEN, BG_BLACK);
   return 0; 

//			OS: 
//	     Memory, Network, Video, Disk, 
//    Keyboard, Mouse, Protection, Programexecution

}


void putchar(unsigned int i, char c, unsigned char fg, unsigned char bg)
{
   char *fb = (char *) 0x000B8000;

   fb[i] = c;
   fb[i+1] = ( (fg & 0x0F) << 4 ) | (bg & 0x0F);
}
void curpos(unsigned short pos)
{
   outb(FB_COMMAND_PORT, FB_HIGH_BYTE_CMD);
   outb(FB_DATA_PORT, ((pos >> 8) & 0x00FF));
   outb(FB_COMMAND_PORT, FB_LOW_BYTE_CMD);
   outb(FB_DATA_PORT, pos & 0x00FF);
}

void clear()
{
	int k = 0;
        int s = 80*25;	

	for(k = 0; k < s; k++)
	{
	   putchar(k*2, ' ', FG_GREEN, BG_BLACK);
	}

}
void putstring(unsigned int i, char c[], unsigned char fg, unsigned char bg)
{
	int k = 0;
        int s = strlen(c);	

	for(k = 0; k < s; k++)
	{
	   putchar(i+k*2, c[k], fg, bg);
	}
}
int strlen(char c[])
{
  int i = 0;
 	
  while( c[i] != '\0')
  {
	i++;
  }
  return i;
}

