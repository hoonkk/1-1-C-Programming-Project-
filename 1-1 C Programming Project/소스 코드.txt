#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
	int game;
	int card,hit;
	int first,second,dealer,player,result;
	int choice;
	int a,b;
	int x,y;
	int i=0;
	int hit1,hit2;
	int chip;
	int blackjack,bacaraat;
	int re;
	srand((unsigned int)time(NULL));

	printf("★★★Welcome to GACHON LAND!★★★\n\n당신은 카지노에 입장하셨습니다.\n\n당신은 초기 자금으로 칩 100개를 지급받습니다.\n");
	getchar();
	chip=100;
	printf("당신은 이곳에서 여러 가지 게임을 통해 칩을 벌 수 있습니다.\n\n당신의 목표는 이 칩을 2배로 불리는 것입니다.\n\n칩을 다 잃게 되면 실패합니다.\n\n자, 이제 게임을 시작합니다.\n");
	getchar();
    start:
	system("cls");
	if(chip<=0)
	{
		system("cls");
		printf("당신은 파산하였습니다. . . \n\n■■■■GAME OVER■■■■\n");

		goto end;
	}
	if(chip>=200)
	{
		system("cls");
		printf("200칩 이상 달성! \n■■■■GAME CLEAR!■■■■\n\n\n\n");

		goto end;
	}
	game:
	printf("\n\n■□뭘 하시겠습니까?□■\n\n\n1.블랙잭(Black Jack)---배팅액:20칩\n\n2.바카라(Bacaraat)---배팅액:5칩\n\n3.가진 칩 확인\n\n4.나가기\n\n");
	scanf("%d",&game);
	if(game==1)
	{
	chip=chip-20;
	system("cls");
	printf("블랙잭을 시작합니다. . .\n\n\n");
	printf("※블랙잭(Black Jack) Rule: 블랙잭은 딜러와 플레이어가 21에 가장 근접한 쪽이\n");
	printf("승리하는 게임입니다. 카드는 10,9,8,7,6,5,4,3,2,A 이렇게 10개가 있는데\n");
	printf("A는 에이스로 1과 11 둘 중 하나로 사용할 수 있습니다.\n\n");
	printf("자, 이제 게임을 시작합니다.\n");
	getchar();
	getchar();
	system("cls");
	
	printf("이제, 딜러와 플레이어는 두 장씩의 카드를 지급받습니다.\n");
	getchar();
	printf("플레이어, 먼저 오픈 카드를 뽑겠습니다.\n");
	getchar();
	card=rand()%10+1;
	{
		if(card>1)
			first=card;
		
		else
		{
			printf("당신은 ACE를 뽑으셨습니다.\n\n1.1로 사용한다.\n2.11로 사용한다.\n\n\n어떻게 하시겠습니까?:");
			
			scanf("%d",&choice);
			switch(choice)
			{
			case 1:
				first=1;
				break;
			case 2:
				first=11;
				break;
			}
		}
	}
	printf("\n\n당신의 첫번째 오픈 카드는 %d입니다.\n\n",first);
	getchar();
	system("cls");
	
	printf("두번째 오픈 카드를 뽑겠습니다.\n\n");
	getchar();
	card=rand()%10+1;
    {
		if(card>1)
			second=card;
		
		else
		{
			printf("당신은 ACE를 뽑으셨습니다.\n\n1.1로 사용한다.\n2.11로 사용한다.\n\n\n당신의 선택은?:");
			
			scanf("%d",&choice);
			switch(choice)
			{
			case 1:
				second=1;
				break;
			case 2:
				second=11;
				break;
			}
		}
	}
	printf("당신의 두번째 오픈카드는 %d입니다.\n\n",second);
	getchar();
	system("cls");
	a=first+second;
	printf("당신의 오픈 카드의 합은 %d입니다.\n\n",a);
	getchar();
	printf("이제 딜러의 차례입니다.\n딜러의 오픈 카드를 확인하겠습니다.\n");
	getchar();
	card=rand()%11+1;
	printf("딜러의 오픈 카드는 %d입니다.\n\n",card);
	dealer=card;
	getchar();
	printf("이제 딜러는 16이상이 될때까지 계속 카드를 지급받습니다.\n\n");
	while(dealer<16){
		card=rand()%11+1;
		dealer=dealer+card;
		i++;

		printf("%d번째 카드를 더 받았습니다.\n\n",i);
		getchar();
	}
	printf("딜러의 카드 배분이 완료되었습니다.\n딜러는 %d까지 카드를 더 받았습니다.\n\n",dealer);
	getchar();
	system("cls");
	printf("<<현재 카드 상황>>\nDealer:%d+Down Card(?)\nPlayer:%d\n\n",dealer,a);
	getchar();
	printf("당신은 이제 당신의 선택에 따라 카드를 더 뽑을 수도 있습니다.\n\n");
	printf("당신은 카드를 받고 싶으면 HIT을, 더 받고 싶지 않으면 STAY를 외치시면 됩니다.\n\n");
	printf("당신이 HIT할 수 있는 횟수는 무한이지만, 숫자가 21을 초과하면 OVER하게되어 패배합니다.\n");
	getchar();
	i=0;
	while(1){
        hit:
		if(a>21){
			printf("당신은 OVER하셨습니다!\n당신은 패배하였습니다.배팅액을 잃습니다.\n");
			getchar();
			goto start;
		}
		printf("1.HIT?\n2.STAY?");
		scanf("%d",&hit);
		if(hit==1)
		{
			card=rand()%10+1;
			printf("HIT하셨습니다. 추가 카드를 받습니다.\n");
			getchar();
			printf("당신의 HIT카드는 %d입니다.\n",card);
			a=a+card;
			i++;
			printf("%d번째 HIT입니다.\n",i);
		}
		if(hit==2)
		{
			printf("STAY하셨습니다.\n다음 단계로 넘어갑니다.\n\n");
			getchar();
			break;
		}
	}
	getchar();
	system("cls");
	printf("<<현재 카드 상황>>\nDealer:%d\nPlayer:%d\n\n",dealer,a);
	printf("\n\n이제 마지막으로 딜러의 다운 카드를 확인합니다.\n\n");
	card=rand()%11+1;
	getchar();
	printf("딜러의 다운 카드는 %d입니다\n\n",card);
	getchar();
	system("cls");
	printf("이제 결과를 발표합니다.\n\n<<결과>>\n\nDealer:%d\nPlayer:%d\n\n",dealer+card,a);
	if(dealer+card>21)
		x=(dealer+card)-21;
	if(dealer+card<=21)
		x=21-(dealer+card);
	y=21-a;
	if(x>y)
	{
		printf("축하합니다, 승리하셨습니다!\n+20CHIPS\n\n");
		chip=chip+40;
		getchar();
		goto start;
	}
	if(x==y)
	{
		printf("당신은 비겼습니다. 배팅액 20칩을 돌려받습니다.");
		chip=chip+20;
		getchar();
		goto start;
	}
	if(x<y)
	{
		printf("아깝습니다, 패배하셨습니다. .\n-20CHIPS\n\n");
		getchar();
		goto start;
	}

	}
	
	if(game==2)
		{
			system("cls");
			printf("바카라를 시작합니다.\n");
			printf("※바카라 Rule: 플레이어는 Player와 Banker 중 하나에 배팅합니다.\n딜러는 그림 카드로 플레이어인지, 뱅커인지 판단합니다.\n");
			printf("플레이어가 맞춘 경우, 배팅액을 2배로 돌려받고 못맞춘 경우 잃게 됩니다.\n\n배팅액은 5칩입니다.\n확인하셨으면 엔터를 누르세요.");
			getchar();
			getchar();
			bacaraat:
			system("cls");
			chip=chip-5;
			printf("Banker와 Player 중, 배팅할 곳을 선택하세요.\n");
			printf("1.Banker\n2.Player\n배팅:");
			scanf("%d",&bacaraat);
			card=rand()%2+1;
			switch(bacaraat)
			{
	case 1:{
			printf("\n\nBanker에 배팅하셨습니다.\n\n");
			if(bacaraat==card)
			{
					printf("그림 카드는 Banker 입니다!\n\n축하합니다, 승리했습니다!\n");
					chip=chip+10;
					goto re;
			}
			if(bacaraat!=card)
			{
				printf("그림 카드는 Player 입니다!\n\n안타깝네요, 패배했습니다. . .\n");
				goto re;
			}
		   }
	case 2:{
		printf("Player에 배팅하셨습니다.\n\n");
		if(bacaraat==card)
		{
			printf("그림 카드는 Player 입니다!\n\n축하합니다, 승리했습니다!\n");
			chip=chip+10;
			goto re;
		}
		if(bacaraat!=card)
		{
			printf("그림 카드는 Banker 입니다!\n\n안타깝네요, 패배했습니다. . . \n");
			goto re;
		}
		
		}
			}
            re:
			printf("AGAIN?    1.REPLAY 2.EXIT\n");
			scanf("%d",&re);

			if(re==1)
				goto bacaraat;
			if(re==2){
				getchar();
				goto start;
			}

	}
			
		
	if(game==3)
		{printf("\n\n\n\n현재 가진 칩의 개수:%d\n\n\n",chip);
	getchar();
	getchar();
	system("cls");
	goto game;
		}

	if(game==4)
	{
		printf("수고하셨습니다! 당신의 수확은 %d칩 이군요.\n",chip-100);
		goto end;
	}

	else
	{
		printf("\n\n\n\n\n잘못 입력하셨네요. 다시 입력하세요.");
		getchar();
		getchar();
		system("cls");
		goto game;
	}
			
	end:
	
			
		
	return 0;
			
}