#include <stdio.h>   
#include <stdlib.h>   
#include <time.h>   
#include <conio.h>   
#include <windows.h>
#include<mmsystem.h>
#pragma comment(lib, "winmm.lib")

void Main_Menu();
int Select_Level();
void Play_Game(int LEVEL);
void Show_man(int life);
void Game_Over();
void gotoxy(short x, short y);

int main()
{
	int LEVEL;

	PlaySound(TEXT("Saw_SoundTrack.wav"), NULL, SND_ASYNC);
	while (1) {
		Main_Menu();
		LEVEL = Select_Level();
		if (LEVEL == -100)
			break;
		if (LEVEL == -10)
			continue;
		Play_Game(LEVEL);
	}

	return 0;
}

void Main_Menu()
{
	system("cls");
	printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛     ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥  ﹥  ﹥﹥﹥  ﹥﹥﹥       弛\n");
	printf("弛     ﹥  ﹥  ﹥  ﹥  ﹥      ﹥      ﹥      ﹥  ﹥  ﹥  ﹥  ﹥           弛\n");
	printf("弛     ﹥﹥﹥  ﹥﹥﹥  ﹥      ﹥      ﹥      ﹥  ﹥  ﹥﹥﹥  ﹥           弛\n");
	printf("弛     ﹥      ﹥ ﹥   ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥  ﹥  ﹥ ﹥   ﹥﹥﹥       弛\n");
	printf("弛     ﹥      ﹥ ﹥   ﹥          ﹥      ﹥  ﹥  ﹥  ﹥ ﹥   ﹥           弛\n");
	printf("弛     ﹥      ﹥  ﹥  ﹥          ﹥      ﹥  ﹥  ﹥  ﹥  ﹥  ﹥           弛\n");
	printf("弛     ﹥      ﹥  ﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥﹥﹥  ﹥  ﹥  ﹥﹥﹥       弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                        	 made by LoGS               弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                  MENU       1. level 1                                   弛\n");
	printf("弛                             2. level 2        choice :                   弛\n");
	printf("弛                             3. level 3                                   弛\n");
	printf("弛                             4. quit                                      弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
}

int Select_Level()
{
	int LEVEL;

	gotoxy(58, 17);
	scanf("%d", &LEVEL);

	if (LEVEL == 1)
		LEVEL = 0;
	else if (LEVEL == 2)
		LEVEL = 3;
	else if (LEVEL == 3)
		LEVEL = 7;
	else if (LEVEL == 4)
		LEVEL = -100;
	else
		LEVEL = -10;

	return LEVEL;
}

void Play_Game(int LEVEL)
{
	char input[3];
	char show[10] = { '_', '_', '_', '_', '_', '_', '_', '_', '_', '_' };
	char word[9][7] = { "mate","time","oral","heart","apink","twice","dejavu","muscle","player" };
	int select, len, unmatched;
	int i, j, life, k = 0;

	srand((unsigned)time(NULL));
	fflush(stdin);
	select = rand() % 3 + LEVEL;
	len = strlen(word[select]);

	for (life = 6; life >= 0; life--) {
		system("cls");
		Show_man(life);

		if (life == 0) {					// LIFE蒂 賅舒 模霞 ц擊 衛 啪歜 謙猿
			Sleep(1000);
			Game_Over();
			break;
		}
		printf("\n");
		for (i = 0; i < len; i++) {				// 欽橫蒂 獗啖場擎 寡翮   // 壽還擊 爾罹輿朝 寡翮
			printf(" %c", show[i]);
		}

		unmatched = 0;
		for (i = 0; i < len; i++) {				// 寡翮 頂縑 樹渦夥陛 氈戲賊 嬴霜 跤蜃轔 旋濠陛 氈擠
			if (show[i] == '_') {
				unmatched = 1;
			}
		}

		if (unmatched == 0) {				// 薑港 殮溘 衛 (樹渦夥陛 橈擊 衛) 轎溘
			printf("\n\nWell Done!\n");
			_getch();
			break;
		}

		printf("\n\nYou Have %d Chance(s)\n", life);			// 陴擎 晦�� 熱
		printf("Wrote Letter : ");

		j = 0;
		for (i = 0; i < k; i++) {				// 殮溘ц湍 僥濠 轎溘    (醞犒 轎溘 熱薑в蹂)
			printf("%c ", input[j]);
			j++;
		}

		printf("\nEnter the letter");
		printf("\n>> ");
		scanf(" %c", &input[k]);

		for (i = 0; i < len; i++) {							// 殮溘ц湍 僥濠 營殮溘 衛 LIFE 模賅 X
			if (input[k] == word[select][i]) {
				show[i] = input[k];
				life++;
			}
		}
		k++;
	}
}

void Show_man(int life)
{
	switch (life) {
	case 0:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                                   ﹥﹥                                   弛\n");
		printf("弛                                    ﹥                                    弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		Sleep(1000); system("cls");
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                                 ﹥﹥﹥﹥                                 弛\n");
		printf("弛                                  ﹥﹥﹥                                  弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		Sleep(1000); system("cls");
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                            ﹥﹥﹥﹥﹥﹥﹥﹥﹥                            弛\n");
		printf("弛                               ﹥﹥﹥﹥﹥﹥                               弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		Sleep(1000); system("cls");
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                     式式式式式式弛Ⅰ８弛式式式式式式                     弛\n");
		printf("弛                           ﹥﹥﹥﹥﹥﹥﹥﹥﹥﹥                           弛\n");
		printf("弛                             ﹥﹥﹥﹥﹥﹥﹥﹥                             弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	case 1:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    式式式式式弛Ⅰ      ８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ忙式忖８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ弛vv弛８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ戌式戎８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ  弛  ８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ戌弛戎８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ  弛  ８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ忙  忖８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ弛  弛８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ弛  弛８弛式式式式式                    弛\n");
		printf("弛                    式式式式式弛Ⅰ      ８弛式式式式式                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	case 2:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    式式式式弛Ⅰ          ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  忙式忖  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  弛QQ弛  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  戌式戎  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ    弛    ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ戌式弛式戎８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ    弛    ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  忙  忖  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  弛  弛  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ  弛  弛  ８弛式式式式                    弛\n");
		printf("弛                    式式式式弛Ⅰ          ８弛式式式式                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	case 3:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    式式式弛Ⅰ              ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    忙式忖    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    弛OO弛    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    戌式戎    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ      弛      ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ戌式式弛式式戎８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ      弛      ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    忙  忖    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    弛  弛    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ    弛  弛    ８弛式式式                    弛\n");
		printf("弛                    式式式弛Ⅰ              ８弛式式式                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	case 4:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    式式弛Ⅰ                  ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      忙式忖      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      弛oo弛      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      戌式戎      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ        弛        ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ戌式式式弛式式式戎８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ        弛        ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      忙  忖      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      弛  弛      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ      弛  弛      ８弛式式                    弛\n");
		printf("弛                    式式弛Ⅰ                  ８弛式式                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	case 5:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    式弛Ⅰ                      ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        忙式忖        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        弛><弛        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        戌式戎        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ          弛          ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ  戌式式式弛式式式戎  ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ          弛          ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        忙  忖        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        弛  弛        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ        弛  弛        ８弛式                    弛\n");
		printf("弛                    式弛Ⅰ                      ８弛式                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
		break;

	default:
		printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                    弛Ⅰ                          ８弛                    弛\n");
		printf("弛                    弛Ⅰ          忙式忖          ８弛                    弛\n");
		printf("弛                    弛Ⅰ          弛^^弛          ８弛                    弛\n");
		printf("弛                    弛Ⅰ          戌式戎          ８弛                    弛\n");
		printf("弛                    弛Ⅰ            弛            ８弛                    弛\n");
		printf("弛                    弛Ⅰ  戌式式式式弛式式式式戎  ８弛                    弛\n");
		printf("弛                    弛Ⅰ            弛            ８弛                    弛\n");
		printf("弛                    弛Ⅰ          忙  忖          ８弛                    弛\n");
		printf("弛                    弛Ⅰ          弛  弛          ８弛                    弛\n");
		printf("弛                    弛Ⅰ          弛  弛          ８弛                    弛\n");
		printf("弛                    弛Ⅰ                          ８弛                    弛\n");
		printf("弛                                                                          弛\n");
		printf("弛                                                                          弛\n");
		printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
	}
}

void Game_Over()
{
	system("cls");
	printf("忙式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式忖\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛     ﹥﹥﹥﹥﹥    ﹥﹥﹥﹥﹥    ﹥﹥﹥﹥﹥    ﹥﹥﹥﹥﹥                 弛\n");
	printf("弛     ﹥            ﹥      ﹥    ﹥  ﹥  ﹥    ﹥                         弛\n");
	printf("弛     ﹥            ﹥      ﹥    ﹥  ﹥  ﹥    ﹥                         弛\n");
	printf("弛     ﹥  ﹥﹥﹥    ﹥﹥﹥﹥﹥    ﹥  ﹥  ﹥    ﹥﹥﹥﹥﹥                 弛\n");
	printf("弛     ﹥      ﹥    ﹥      ﹥    ﹥  ﹥  ﹥    ﹥                         弛\n");
	printf("弛     ﹥      ﹥    ﹥      ﹥    ﹥  ﹥  ﹥    ﹥                         弛\n");
	printf("弛     ﹥﹥﹥﹥﹥    ﹥      ﹥    ﹥  ﹥  ﹥    ﹥﹥﹥﹥﹥                 弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                                          弛\n");
	printf("弛              ﹥﹥﹥﹥﹥    ﹥      ﹥    ﹥﹥﹥﹥﹥    ﹥﹥﹥﹥﹥        弛\n");
	printf("弛              ﹥      ﹥    ﹥      ﹥    ﹥            ﹥      ﹥        弛\n");
	printf("弛              ﹥      ﹥     ﹥    ﹥     ﹥            ﹥      ﹥        弛\n");
	printf("弛              ﹥      ﹥     ﹥    ﹥     ﹥﹥﹥﹥﹥    ﹥﹥﹥﹥﹥        弛\n");
	printf("弛              ﹥      ﹥      ﹥  ﹥      ﹥            ﹥  ﹥            弛\n");
	printf("弛              ﹥      ﹥      ﹥  ﹥      ﹥            ﹥    ﹥          弛\n");
	printf("弛              ﹥﹥﹥﹥﹥       ﹥﹥       ﹥﹥﹥﹥﹥    ﹥      ﹥        弛\n");
	printf("弛                                                                          弛\n");
	printf("弛                                                      PRESS ANY KEY       弛\n");
	printf("戌式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式式戎\n");
	_getch();
}

void gotoxy(short x, short y)
{
	COORD Pos = { x,y };
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), Pos);
}