# KentRepository
package bowlingTest;

public class Game {
	 private int rolls[] = new int[21];
	  private int currentRoll = 0;

	  public void roll(int pins) {
		 	 rolls[currentRoll++] = pins;
	  }
		 	public static void main(String[] args) {
				int input;
				int ballthrow;
				int frame;
				int roll;
				int[] a = {1,4,4,5,6,4,5,5,10,0,0,1,7,3,6,4,10,0,2,8,6};
				Game bowl=new Game();
				for(ballthrow=0;ballthrow<=20;ballthrow++)
				{
					frame=(ballthrow/2)+1;
					roll=(ballthrow%2)+1;
					input=a[ballthrow];
					if(input<=10&&input>=0)
						bowl.roll(input);
					else if(input>10||input<0){
							ballthrow--;
							}
						else if(input==10)
							ballthrow++;
				}
			        System.out.println(bowl.score(bowl.rolls));
			}
		int score(int[] a){
				int scr=0;
				int i;
				for(i=0;i<=20;i++)
				{
					if(i==2){
						if((a[i-1]+a[i-2]==10)){
							scr=scr+(2*a[i]);
						}
						else{
							scr=scr+a[i];
						}
					}
					else if((i>2)&&i!=20)
							{
							if((a[i-1]+a[i-2]==10)&&(i%2==0))
							{
								scr=scr+(2*a[i]);
							}
							else if((a[i-3]==10)&&(i%2==1))
										{
											scr=scr+2*(a[i]);
										}
								else
								{
									scr=scr+a[i];
							}
							if(i>3&&(a[i-2]==10&&a[i-4]==10))
							{
								scr=scr+a[i];
							}
							else if(i>3&&(a[i-3]==10&&a[i-5]==10)&&i%2==1){
								scr=scr+a[i];
							}
							}
						else{
							scr=scr+a[i];
							}
				}
				return scr;
			}
			

}
