# Java-Final-Project
## Team Members: Feridun Mujde, Karshiboev Aibek, Jumabaev Kurmanbek
![Снимок экрана (9)](https://user-images.githubusercontent.com/81102375/117619435-12e05c80-b191-11eb-99f0-c6d6e97dc4cd.png)

## Explanation of the game
###### Minesweeper is a single-player puzzle game
######  The objective of the game is to clear a rectangular board containing hidden "mines" or bombs without detonating any of them, with help from clues about the number of neighboring mines in each field.

# Codes

## Initialising Screen
```
    public MineField() {
        openButton = 0;
        frame = new JFrame("Field of Bombs");
        frame.setExtendedState( frame.getExtendedState()|JFrame.MAXIMIZED_BOTH );

        frame.setSize(1000, 1000);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(new GridLayout(10, 10));

        for (int row = 0; row < board.length; row++) {
            for (int col = 0; col < board[0].length; col++) {
                Btn b = new Btn(row, col);
                frame.add(b);
                b.addMouseListener(this);
                board[row][col] = b;
            }
        }

```
## Buttons
```
import javax.swing.JButton;



public class Btn extends JButton{
    private int row,col,count;
    private boolean mine,flag;



    public Btn(int row, int col) {
        this.row = row;
        this.col = col;
        this.count = 0;
        this.mine = false;
        this.flag = false;
    }

public class MineField implements MouseListener {
    JFrame frame;
    Btn[][] board = new Btn[10][10];
    int openButton;
```
```
    public MineField() {
        openButton = 0;
        frame = new JFrame("Field of Bombs");
        frame.setExtendedState( frame.getExtendedState()|JFrame.MAXIMIZED_BOTH );
```    

## Creating Mine
```
        generateMine();
        updateCount();


        frame.setVisible(true);
    }



    public void generateMine() {
        int i = 0;
        while (i < 10) {
            int randRow = (int) (Math.random() * board.length);
            int randCol = (int) (Math.random() * board[0].length);

            while (board[randRow][randCol].isMine()) {
                randRow = (int) (Math.random() * board.length);
                randCol = (int) (Math.random() * board[0].length);
            }
            board[randRow][randCol].setMine(true);
            i++;
        }
    }
