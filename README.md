# Java-Final-Project
## Team Members: Feridun Mujde, Karshiboev Aibek, Jumabaev Kurmanbek
![Снимок экрана (9)](https://user-images.githubusercontent.com/81102375/117619435-12e05c80-b191-11eb-99f0-c6d6e97dc4cd.png)

## Explanation of the game
###### Minesweeper is a single-player puzzle game
######  The objective of the game is to clear a rectangular board containing hidden "mines" or bombs without detonating any of them, with help from clues about the number of neighboring mines in each field.

### Trello screenshots:
![photo5244524002268001012](https://user-images.githubusercontent.com/81102375/117640617-fe0ec380-b1a6-11eb-9b8e-c29a7e4bf748.jpg)


### Trello link:
[https://trello.com/b/cArs8vfG/pl-project](url)


### Figma design:
![Снимок экрана (15)](https://user-images.githubusercontent.com/81102375/117640364-c6a01700-b1a6-11eb-992d-195e10fadcca.png)

### Figma link:
[https://www.figma.com/file/xCurctD5wSVDgMkuCrkyTJ/Untitled?node-id=0:1](url)
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
## Setting up The Game    
```
    public void open(int r, int c) {
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length || board[r][c].getText().length() > 0
                || board[r][c].isEnabled() == false) {
            return;
        } else if (board[r][c].getCount() != 0) {
            board[r][c].setText(board[r][c].getCount() + "");
            board[r][c].setEnabled(false);
            openButton++;
        } else {
            openButton++;
            board[r][c].setEnabled(false);
            open(r - 1, c);
            open(r + 1, c);
            open(r, c - 1);
            open(r, c + 1);
        }
    }

```

