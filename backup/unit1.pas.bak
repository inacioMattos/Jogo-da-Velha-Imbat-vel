unit Unit1;

{$mode objfpc}{$H+}

interface

uses
    Classes, SysUtils, sqldb, FileUtil, TASources, TAStyles, TAGraph,
    CheckBoxThemed, RTTICtrls, Forms, Controls, Graphics, Dialogs, ExtCtrls,
    StdCtrls, Arrow, ButtonPanel, ColorBox, Grids, Buttons, ComCtrls;

type

    { TForm1 }
    TArr = array [0..9999, 0..10] of Integer;
    TForm1 = class(TForm)
        btnVsCPU: TButton;
        btnVsP2: TButton;
        btnOnline: TButton;
        Button1: TButton;
        btnVoltarMenu: TButton;
        btnOptions: TButton;
        Button2: TButton;
        btnBusca: TButton;
        ComboBox1: TComboBox;
        Label1: TLabel;
        Label10: TLabel;
        Label3: TLabel;
        Label4: TLabel;
        Label5: TLabel;
        Label6: TLabel;
        Label7: TLabel;
        Label8: TLabel;
        Label9: TLabel;
        labelP2: TLabel;
        labelTie: TLabel;
        libe: TLabel;
        libe1: TLabel;
        libe2: TLabel;
        lScoreP1: TLabel;
        lScoreP2: TLabel;
        lScoreP3: TLabel;
        lWelcome: TLabel;
        Label2: TLabel;
        panelOptions: TPanel;
        panelGame: TPanel;
        panelInicio: TPanel;
        Shape10: TShape;
        Shape11: TShape;
        Shape12: TShape;
        Shape13: TShape;
        Shape2: TShape;
        Shape3: TShape;
        Shape1: TShape;
        Shape6: TShape;
        Shape5: TShape;
        Shape4: TShape;
        Shape9: TShape;
        Shape8: TShape;
        Shape7: TShape;
        Timer1: TTimer;



        procedure btnBuscaMouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure btnOptionsClick(Sender: TObject);
        procedure btnVoltarMenuClick(Sender: TObject);
        procedure btnVsCPUClick(Sender: TObject);
        procedure btnVsP2Click(Sender: TObject);
        procedure Button1Click(Sender: TObject);
        procedure Button2Click(Sender: TObject);
        procedure clickTabuleiro(obj: TShape);
        procedure attBoard();
        procedure FormCreate(Sender: TObject);
        procedure FormPaint(Sender: TObject);
        procedure letra(obj: TShape; letra: String);
        procedure init();
        procedure stateOfGame();
        procedure endGame(state: Integer);
        procedure ai();

        function win(tab: TArr; player: Integer): Integer;
        function availableSpots(tab: TArr): TArr;
        function busca(tab: TArr; player: Integer): TArr;

        procedure Shape1ChangeBounds(Sender: TObject);
        procedure Shape1MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape1MouseEnter(Sender: TObject);
        procedure Shape1MouseLeave(Sender: TObject);
        procedure Shape2MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape2MouseEnter(Sender: TObject);
        procedure Shape2MouseLeave(Sender: TObject);
        procedure Shape3MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape3MouseEnter(Sender: TObject);
        procedure Shape3MouseLeave(Sender: TObject);
        procedure Shape4MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape4MouseEnter(Sender: TObject);
        procedure Shape4MouseLeave(Sender: TObject);
        procedure Shape4Paint(Sender: TObject);
        procedure Shape5MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape5MouseEnter(Sender: TObject);
        procedure Shape5MouseLeave(Sender: TObject);
        procedure Shape6MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape6MouseEnter(Sender: TObject);
        procedure Shape6MouseLeave(Sender: TObject);
        procedure Shape7MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape7MouseEnter(Sender: TObject);
        procedure Shape7MouseLeave(Sender: TObject);
        procedure Shape8MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape8MouseEnter(Sender: TObject);
        procedure Shape8MouseLeave(Sender: TObject);
        procedure Shape9MouseDown(Sender: TObject; Button: TMouseButton;
            Shift: TShiftState; X, Y: Integer);
        procedure Shape9MouseEnter(Sender: TObject);
        procedure Shape9MouseLeave(Sender: TObject);
        procedure Timer1Timer(Sender: TObject);
    private
        { private declarations }
    public
        { public declarations }
    end;

var
    Form1: TForm1;
    tabuleiro: TArr;
    bool: Integer = 0;
    turno: Integer = 1;
    cpu: Integer = 0;

    p1Score: Integer = 0;
    p2Score: Integer = 0;
    ties: Integer = 0;

    X: Integer = 0;
    O: Integer = 1;


    // vars ai {{{NÃO MEXE PLOX}}}
    aiNivel: Integer = 0;
    turnoAtual: Integer = 1;
    fc: Integer = 0;
    re: TArr;


//####################################################################
//     █████  ███    ██ ██ ███    ███  █████   ██████  █████   ██████
//    ██   ██ ████   ██ ██ ████  ████ ██   ██ ██      ██   ██ ██    ██
//    ███████ ██ ██  ██ ██ ██ ████ ██ ███████ ██      ███████ ██    ██
//    ██   ██ ██  ██ ██ ██ ██  ██  ██ ██   ██ ██      ██   ██ ██    ██
//    ██   ██ ██   ████ ██ ██      ██ ██   ██  ██████ ██   ██  ██████
//####################################################################

    TopNormal: Integer = 128;       // altura normalmente dos bloquinhos
    WidthNormal: Integer = 128;     // comprimento normalmente dos bloquinhos

    MaxTop: Integer = 136;      // altura maxima que a animação irá chegar
    MaxWidth: Integer = 136;    // comprimento maximo que a animação irá chegar

    incrementoHeight: Real = 0.22;  // a velocidade que a transição irá acontecer.
                        //  ^^^^^^ -> {{{QUANTO MAIOR O NUMERO MAIS RAPIDO SERA AS ANIMACOES}}}

    incrementoWidth: Real = 0.22;   // NÃO MEXE AQUI!!!!!!!!!!!!!!!!!!!!

    arrAnimValues: array [0..8, 0..1] of Real;  // NEM AQUI!
    arrHover: array [0..8] of Integer;  // MUITO MENOS AQUI!


//####################################################################
//     ██████  ██████  ██████  ███████ ███████
//    ██      ██    ██ ██   ██ ██      ██
//    ██      ██    ██ ██████  █████   ███████
//    ██      ██    ██ ██   ██ ██           ██
//     ██████  ██████  ██   ██ ███████ ███████
//####################################################################

    // VERMELHO = $003643F4
    // INDIGO (MEIO AZUL MEIO ROXO) = $00B5513F
    // INDIGO CLARO = $00E87C75
    // BRANCO = $00FAFAFA
    // PRETO = $00212121
    // VERDE = $0050AF4C
    // CIANO (VERDE PUXADO P AZUL) = $00889600
    // ROSA = $008140FF
    // ROSA ESCURO = $005500C6

    colorBg: TColor = $00B5513F;    // cor do fundo
    colorBgBtn: TColor = $00FAFAFA;     // cor do fundo dos bloquinhos
    colorX: TColor = $005500C6;     // cor do X
    colorO: TColor = $008140FF;     // cor do O

    //colorBg: TColor = $00B5513F;
    //colorBgBtn: TColor = $00FAFAFA;
    //colorX: TColor = $005500C6;
    //colorO: TColor = $008140FF;



implementation

{$R *.lfm}


procedure TForm1.init();
var
    i: Integer = 0;
    x: Integer;
begin
    Form1.Color := colorBg;

    Shape1.Brush.Color := colorBgBtn;
    Shape2.Brush.Color := colorBgBtn;
    Shape3.Brush.Color := colorBgBtn;
    Shape4.Brush.Color := colorBgBtn;
    Shape5.Brush.Color := colorBgBtn;
    Shape6.Brush.Color := colorBgBtn;
    Shape7.Brush.Color := colorBgBtn;
    Shape8.Brush.Color := colorBgBtn;
    Shape9.Brush.Color := colorBgBtn;

    turno := 1;


    if (cpu = 0) then
    begin
        libe.Caption := 'P1';
        libe.Left := 88;

        Shape11.Left := 64;
        Shape11.Width := 88;

        lScoreP1.Left := 101;


        labelP2.Caption := 'P2';
    end
    else begin
        libe.Caption := 'Você';
        libe.Left := 80;

        Shape11.Left := 40;
        Shape11.Width := 171;

        lScoreP1.Left := 118;

        labelP2.Caption := 'PC';
    end;


    while (i < 3) do
    begin
        x := 0;
        while (x < 3) do
        begin
            tabuleiro[i, x] := 0;
            x := x + 1;
        end;
        i := i + 1;
    end;

    i := 0;

    while (i < 9) do
    begin
        x := 0;
        while (x < 2) do
        begin
            arrAnimValues[i, x] := 0;
            x := x + 1;
        end;
        arrHover[i] := 0;
        i := i + 1;
    end;

    Label1.Visible := False;
    Label2.Visible := False;
    Label3.Visible := False;
    Label4.Visible := False;
    Label5.Visible := False;
    Label6.Visible := False;
    Label7.Visible := False;
    Label8.Visible := False;
    Label9.Visible := False;

    turno := 1;

end;


procedure TForm1.endGame(state: Integer);
var
    temp: Integer = 0;
begin
    if (state = 1) then
    begin
        //ShowMessage(IntToStr(win(tabuleiro, 1)));
        ShowMessage('X venceu a partida ;D.');
        if (X = 0) then
        begin
            p1Score := p1Score + 1;
        end
        else begin
            p2Score := p2Score + 1;
        end;
    end;
    if (state = -1) then
    begin
        //ShowMessage(IntToStr(win(tabuleiro, 1)));
        ShowMessage('○ venceu a partida ;D.');
        if (O = 0) then
        begin
            p1Score := p1Score + 1;
        end
        else begin
            p2Score := p2Score + 1;
        end;
    end;
    if (state = 0) then
    begin
        //ShowMessage(IntToStr(win(tabuleiro, 1)));
        ShowMessage('putz, ocorreu um empate :/.');
        ties := ties + 1;
    end;

    if (not (state = 2)) then
    begin
        if (not (cpu = 1)) then
        begin
            temp := O;
            O := X;
            X := temp;
        end;

        init();
    end;

end;


procedure TForm1.stateOfGame();
var
    state: Integer = 2;
begin
    // HORIZONTAISSSSS
    if ((tabuleiro[0, 0] = tabuleiro[1, 0]) and (tabuleiro[0, 0] = tabuleiro[2, 0])) then
    begin
        if (tabuleiro[0, 0] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[0, 0] = -1) then
        begin
            endGame(-1);
        end;
    end;
    if ((tabuleiro[0, 1] = tabuleiro[1, 1]) and (tabuleiro[0, 1] = tabuleiro[2, 1])) then
    begin
        if (tabuleiro[0, 1] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[0, 1] = -1) then
        begin
            endGame(-1);
        end;
    end;
    if ((tabuleiro[0, 2] = tabuleiro[1, 2]) and (tabuleiro[0, 2] = tabuleiro[2, 2])) then
    begin
        if (tabuleiro[0, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[0, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;


    // VERTICAIS
    if ((tabuleiro[0, 2] = tabuleiro[0, 1]) and (tabuleiro[0, 2] = tabuleiro[0, 0])) then
    begin
        if (tabuleiro[0, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[0, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;
    if ((tabuleiro[1, 2] = tabuleiro[1, 1]) and (tabuleiro[1, 2] = tabuleiro[1, 0])) then
    begin
        if (tabuleiro[1, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[1, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;
    if ((tabuleiro[2, 2] = tabuleiro[2, 1]) and (tabuleiro[2, 2] = tabuleiro[2, 0])) then
    begin
        if (tabuleiro[2, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[2, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;


    // DIAGONAIS
    if ((tabuleiro[2, 2] = tabuleiro[1, 1]) and (tabuleiro[2, 2] = tabuleiro[0, 0])) then
    begin
        if (tabuleiro[2, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[2, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;
    if ((tabuleiro[0, 2] = tabuleiro[1, 1]) and (tabuleiro[0, 2] = tabuleiro[2, 0])) then
    begin
        if (tabuleiro[0, 2] = 1) then
        begin
            endGame(1);
        end;
        if (tabuleiro[0, 2] = -1) then
        begin
            endGame(-1);
        end;
    end;


    if ( (not (tabuleiro[0, 0] = 0)) and (not (tabuleiro[0, 1] = 0)) and (not (tabuleiro[0, 2] = 0)) and (not (tabuleiro[1, 0] = 0)) and (not (tabuleiro[1, 1] = 0)) and (not (tabuleiro[1, 2] = 0)) and (not (tabuleiro[2, 0] = 0)) and (not (tabuleiro[2, 1] = 0)) and (not (tabuleiro[2, 2] = 0))) then
    begin
        endGame(0);
    end;

end;


procedure TForm1.ai();
var
    c: String;
    line: Integer;
    col: Integer;
begin
    if (availableSpots(tabuleiro)[0, 0] = 8) then
    begin
        if (tabuleiro[1, 1] = 1) then
        begin
            re[1, 0] := 0;
            re[1, 1] := 0;
        end
        else begin
            re[1, 0] := 1;
            re[1, 1] := 1;
        end;
    end
    else begin
        re := busca(tabuleiro, -1);
        //ShowMessage(IntToStr(fc));
    end;

    line := re[1, 0];
    col := re[1, 1];

    fc := 0;

    if (X = 1) then
    begin
        tabuleiro[re[1, 0], re[1, 1]] := 1;
        c := 'X';
    end
    else begin
        tabuleiro[re[1, 0], re[1, 1]] := -1;
        c := 'O';
    end;


    if ((line = 0) and (col = 0)) then
    begin
        letra(Shape1, c);
    end;
    if ((line = 0) and (col = 1)) then
    begin
        letra(Shape2, c);
    end;
    if ((line = 0) and (col = 2)) then
    begin
        letra(Shape3, c);
    end;

    if ((line = 1) and (col = 0)) then
    begin
        letra(Shape4, c);
    end;
    if ((line = 1) and (col = 1)) then
    begin
        letra(Shape5, c);
    end;
    if ((line = 1) and (col = 2)) then
    begin
        letra(Shape6, c);
    end;

    if ((line = 2) and (col = 0)) then
    begin
        letra(Shape7, c);
    end;
    if ((line = 2) and (col = 1)) then
    begin
        letra(Shape8, c);
    end;
    if ((line = 2) and (col = 2)) then
    begin
        letra(Shape9, c);
    end;



    turno := turno * -1;

    stateOfGame();
end;


function TForm1.win(tab: TArr; player: Integer): Integer;
var
    t: Integer = 2;
begin
    win := t;

    if ( (not (tab[0, 0] = 0)) and (not (tab[0, 1] = 0)) and (not (tab[0, 2] = 0)) and (not (tab[1, 0] = 0)) and (not (tab[1, 1] = 0)) and (not (tab[1, 2] = 0)) and (not (tab[2, 0] = 0)) and (not (tab[2, 1] = 0)) and (not (tab[2, 2] = 0))) then
    begin
        t := (0);
        win := 0;
    end;

    if ((tab[0, 0] = tab[1, 0]) and (tab[0, 0] = tab[2, 0])) then
    begin
        if (tab[0, 0] = 1) then
        begin
            t := 1;
        end;
        if (tab[0, 0] = -1) then
        begin
            t := (-1);
        end;
    end;
    if ((tab[0, 1] = tab[1, 1]) and (tab[0, 1] = tab[2, 1])) then
    begin
        if (tab[0, 1] = 1) then
        begin
            t := (1);
        end;
        if (tab[0, 1] = -1) then
        begin
            t := (-1);
        end;
    end;
    if ((tab[0, 2] = tab[1, 2]) and (tab[0, 2] = tab[2, 2])) then
    begin
        if (tab[0, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[0, 2] = -1) then
        begin
            t := (-1);
        end;
    end;


    // VERTICAIS
    if ((tab[0, 2] = tab[0, 1]) and (tab[0, 2] = tab[0, 0])) then
    begin
        if (tab[0, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[0, 2] = -1) then
        begin
            t := (-1);
        end;
    end;
    if ((tab[1, 2] = tab[1, 1]) and (tab[1, 2] = tab[1, 0])) then
    begin
        if (tab[1, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[1, 2] = -1) then
        begin
            t := (-1);
        end;
    end;
    if ((tab[2, 2] = tab[2, 1]) and (tab[2, 2] = tab[2, 0])) then
    begin
        if (tab[2, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[2, 2] = -1) then
        begin
            t := (-1);
        end;
    end;


    // DIAGONAIS
    if ((tab[2, 2] = tab[1, 1]) and (tab[2, 2] = tab[0, 0])) then
    begin
        if (tab[2, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[2, 2] = -1) then
        begin
            t := (-1);
        end;
    end;
    if ((tab[0, 2] = tab[1, 1]) and (tab[0, 2] = tab[2, 0])) then
    begin
        if (tab[0, 2] = 1) then
        begin
            t := (1);
        end;
        if (tab[0, 2] = -1) then
        begin
            t := -1;
        end;
    end;





    if (t = 1) then
    begin
        if (X = 0) then
        begin
            win := -10;
        end
        else begin
            win := 10;
        end;
    end;

    if (t = -1) then
    begin
        if (O = 0) then
        begin
            win := -10;
        end
        else begin
            win := 10;
        end;
    end;
end;

function TForm1.busca(tab: TArr; player: Integer): TArr;
var
    availSpots: TArr;
    moves: array [0..9999, 0..2] of Integer;
    i: Integer = 1;
    x: Integer = 0;
    count: Integer = 0;
    r: TArr;
    bestMove: array [0..1] of Integer;
    bestScore: Integer;
begin
    fc := fc + 1;
    //ShowMessage('inicio buscaaaa');
    availSpots := availableSpots(tab);

    if (win(tab, player) = 10) then
    begin
        busca[0, 0] := 10;
    end;
    if (win(tab, player) = 0) then
    begin
        busca[0, 0] := 0;
    end;
    if (win(tab, player) = -10) then
    begin
        busca[0, 0] := -10;
    end;

    if (win(tab, player) = 2) then
    begin
        //application.messagebox('player é 2.', 'a', 0);
        busca[0, 0] := -1;

        while (i < availSpots[0, 0] + 1) do
        begin
            //application.messagebox('whilezao', 'a', 0);
            moves[count, 0] := availSpots[i, 0];
            moves[count, 1] := availSpots[i, 1];

            // marcar no tabuleiro o correto da jogada atual
            if (player = -1) then
            begin
                if (X = 1) then
                begin
                    tab[availSpots[i, 0], availSpots[i, 1]] := 1;
                end
                else begin
                    tab[availSpots[i, 0], availSpots[i, 1]] := -1;
                end;
            end
            else begin
                if (X = 0) then
                begin
                    tab[availSpots[i, 0], availSpots[i, 1]] := 1;
                end
                else begin
                    tab[availSpots[i, 0], availSpots[i, 1]] := -1;
                end;
            end;

            r := busca(tab, player * -1);
            moves[count, 2] := r[0, 0];

            tab[moves[count, 0], moves[count, 1]] := 0;

            count := count + 1;
            i := i + 1;
        end;
        //ShowMessage('SAIA WHILEASDA');
        if (player = -1) then
        begin
            bestScore := -10000;

            i := 0;
            while (i < count) do
            begin

                if (moves[i, 2] > bestScore) then
                begin
                    bestScore := moves[i, 2];

                    bestMove[0] := moves[i, 0];
                    bestMove[1] := moves[i, 1];
                end;

                i := i + 1;
            end;
        end
        else begin
            bestScore := 10000;

            i := 0;
            while (i < count) do
            begin
                if (moves[i, 2] < bestScore) then
                begin
                    bestScore := moves[i, 2];

                    bestMove[0] := moves[i, 0];
                    bestMove[1] := moves[i, 1];
                end;

                i := i + 1;
            end;
        end;

        busca[0, 0] := bestScore;
        busca[1, 0] := bestMove[0];
        busca[1, 1] := bestMove[1];
        //ShowMessage('f1111111nalllll');
    end;
end;


function TForm1.availableSpots(tab: TArr): TArr;
var
    i: Integer = 0;
    x: Integer = 0;
    count: Integer = 0;
begin
    //ShowMessage('inicio spots co dardacalcuiacofhasdiuo');
    while (i < 3) do
    begin
        x := 0;
        while (x < 3) do
        begin
            //ShowMessage(IntToStr(tab[i, x]));
            if (tab[i, x] = 0) then
            begin
                count := count + 1;
                //application.messagebox('count++', 'a', 0);
                availableSpots[count, 0] := i;
                availableSpots[count, 1] := x;
            end;
            x := x + 1;
        end;
        i := i + 1;
    end;
    availableSpots[0, 0] := count;
end;


procedure TForm1.clickTabuleiro(obj: TShape);
var
    c: String;
    wasAPlay: Integer = 0;
begin
    if (turno = 1)then
    begin
        c := 'X';
    end
    else begin
        c := 'O';
    end;

    if (((cpu = 1) and (X = 0) and (turno = 1)) or ( (cpu = 1) and (O = 0) and (turno = -1) ) or (cpu = 0) ) then
    begin
        if ((obj.Name = 'Shape1') and (tabuleiro[0, 0] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[0, 0] := turno;
            letra(Shape1, c);
        end;

        if ((obj.Name = 'Shape2') and (tabuleiro[0, 1] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[0, 1] := turno;
            letra(Shape2, c);
        end;

        if ((obj.Name = 'Shape3') and (tabuleiro[0, 2] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[0, 2] := turno;
            letra(Shape3, c);
        end;

        if ((obj.Name = 'Shape4') and (tabuleiro[1, 0] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[1, 0] := turno;
            letra(Shape4, c);
        end;

        if ((obj.Name = 'Shape5') and (tabuleiro[1, 1] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[1, 1] := turno;
            letra(Shape5, c);
        end;

        if ((obj.Name = 'Shape6') and (tabuleiro[1, 2] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[1, 2] := turno;
            letra(Shape6, c);
        end;

        if ((obj.Name = 'Shape7') and (tabuleiro[2, 0] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[2, 0] := turno;
            letra(Shape7, c);
        end;

        if ((obj.Name = 'Shape8') and (tabuleiro[2, 1] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[2, 1] := turno;
            letra(Shape8, c);
        end;

        if ((obj.Name = 'Shape9') and (tabuleiro[2, 2] = 0)) then
        begin
            wasAPlay := 1;
            tabuleiro[2, 2] := turno;
            letra(Shape9, c);
        end;

        if (wasAPlay = 1) then
        begin
            turno := turno * -1;
        end;

        stateOfGame();

        if ((cpu = 1) and (X = 1) and (turno = 1)) then
        begin
            ai();
        end;
        if ((cpu = 1) and (X = 0) and (turno = -1)) then
        begin
            ai();
        end;
    end;

end;

procedure TForm1.Button1Click(Sender: TObject);
begin
    init();
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
    panelOptions.Left := 999;
    panelOptions.Visible := False;

    panelInicio.Left := 0;
    panelInicio.Visible := True;
end;

procedure TForm1.btnVoltarMenuClick(Sender: TObject);
begin
    panelGame.Left := 999;
    panelGame.Visible := False;

    panelInicio.Left := 0;
    panelInicio.Visible := True;
end;

procedure TForm1.btnOptionsClick(Sender: TObject);
begin
    panelInicio.Left := 999;
    panelInicio.Visible := False;

    panelOptions.Left := 0;
    panelOptions.Visible := True;
end;

procedure TForm1.btnBuscaMouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
var
   k: TArr;
begin
    k := busca(tabuleiro, turno);
    ShowMessage(IntToStr(k[0, 0]) + ' :::[' + IntToStr(k[1, 0]) + ', ' + IntToStr(k[1, 1]) + ']');
end;

procedure TForm1.btnVsCPUClick(Sender: TObject);
begin
    panelInicio.Left := 999;
    panelInicio.Visible := False;

    panelGame.Left := 0;
    panelGame.Visible := True;

    if (cpu = 0) then
    begin
        p1Score := 0;
        p2Score := 0;
        ties := 0;

        turno := 1;

        cpu := 1;
        init();
    end;
end;

procedure TForm1.btnVsP2Click(Sender: TObject);
begin
    panelInicio.Left := 999;
    panelInicio.Visible := False;

    panelGame.Left := 0;
    panelGame.Visible := True;

    if (cpu = 1) then
    begin
        p1Score := 0;
        p2Score := 0;
        ties := 0;

        turno := 1;

        cpu := 0;
        init();
    end;


end;


procedure TForm1.attBoard();
begin
    if (tabuleiro[0, 0] = 1) then
    begin
        letra(Shape1, 'X');
    end;
    if (tabuleiro[0, 1] = 1) then
    begin
        letra(Shape2, 'X');
    end;
    if (tabuleiro[0, 2] = 1) then
    begin
        letra(Shape3, 'X');
    end;
    if (tabuleiro[1, 0] = 1) then
    begin
        letra(Shape4, 'X');
    end;
    if (tabuleiro[1, 1] = 1) then
    begin
        letra(Shape5, 'X');
    end;
    if (tabuleiro[1, 2] = 1) then
    begin
        letra(Shape6, 'X');
    end;
    if (tabuleiro[2, 0] = 1) then
    begin
        letra(Shape7, 'X');
    end;
    if (tabuleiro[2, 1] = 1) then
    begin
        letra(Shape8, 'X');
    end;
    if (tabuleiro[2, 2] = 1) then
    begin
        letra(Shape9, 'X');
    end;


    if (tabuleiro[0, 0] = -1) then
    begin
        letra(Shape1, 'O');
    end;
    if (tabuleiro[0, 1] = -1) then
    begin
        letra(Shape2, 'O');
    end;
    if (tabuleiro[0, 2] = -1) then
    begin
        letra(Shape3, 'O');
    end;
    if (tabuleiro[1, 0] = -1) then
    begin
        letra(Shape4, 'O');
    end;
    if (tabuleiro[1, 1] = -1) then
    begin
        letra(Shape5, 'O');
    end;
    if (tabuleiro[1, 2] = -1) then
    begin
        letra(Shape6, 'O');
    end;
    if (tabuleiro[2, 0] = -1) then
    begin
        letra(Shape7, 'O');
    end;
    if (tabuleiro[2, 1] = -1) then
    begin
        letra(Shape8, 'O');
    end;
    if (tabuleiro[2, 2] = -1) then
    begin
        letra(Shape9, 'O');
    end;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
    init();
end;

procedure TForm1.FormPaint(Sender: TObject);
begin

end;


procedure TForm1.letra(obj: TShape; letra: String);
var
    l: TLabel;
    colorFont: TColor;
begin
    if (letra = 'X') then
    begin
        colorFont := colorX;
    end
    else begin
        colorFont := colorO;
    end;

    if (obj.Name = 'Shape1') then
    begin
        Label1.Caption := letra;
        Label1.Left := obj.Left + 40;
        Label1.Top := obj.Top + 20;
        Label1.Visible := True;
        Label1.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape2') then
    begin
        Label2.Caption := letra;
        Label2.Left := obj.Left + 40;
        Label2.Top := obj.Top + 20;
        Label2.Visible := True;
        Label2.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape3') then
    begin
        Label3.Caption := letra;
        Label3.Left := obj.Left + 40;
        Label3.Top := obj.Top + 20;
        Label3.Visible := True;
        Label3.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape4') then
    begin
        Label4.Caption := letra;
        Label4.Left := obj.Left + 40;
        Label4.Top := obj.Top + 20;
        Label4.Visible := True;
        Label4.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape5') then
    begin
        Label5.Caption := letra;
        Label5.Left := obj.Left + 40;
        Label5.Top := obj.Top + 20;
        Label5.Visible := True;
        Label5.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape6') then
    begin
        Label6.Caption := letra;
        Label6.Left := obj.Left + 40;
        Label6.Top := obj.Top + 20;
        Label6.Visible := True;
        Label6.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape7') then
    begin
        Label7.Caption := letra;
        Label7.Left := obj.Left + 40;
        Label7.Top := obj.Top + 20;
        Label7.Visible := True;
        Label7.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape8') then
    begin
        Label8.Caption := letra;
        Label8.Left := obj.Left + 40;
        Label8.Top := obj.Top + 20;
        Label8.Visible := True;
        Label8.Font.Color := colorFont
    end;

    if (obj.Name = 'Shape9') then
    begin
        Label9.Caption := letra;
        Label9.Left := obj.Left + 40;
        Label9.Top := obj.Top + 20;
        Label9.Visible := True;
        Label9.Font.Color := colorFont
    end;


end;

procedure TForm1.Shape1ChangeBounds(Sender: TObject);
begin

end;

procedure TForm1.Shape1MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape1);
end;

procedure TForm1.Shape1MouseEnter(Sender: TObject);
begin
    arrHover[0] := 1;
    arrAnimValues[0 ,0] := 0;
end;

procedure TForm1.Shape1MouseLeave(Sender: TObject);
begin
    arrHover[0] := 0;
    arrAnimValues[0 ,0] := 0;
end;

procedure TForm1.Shape2MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape2);
end;

procedure TForm1.Shape2MouseEnter(Sender: TObject);
begin
    arrHover[1] := 1;
    arrAnimValues[1 ,0] := 0;
end;

procedure TForm1.Shape2MouseLeave(Sender: TObject);
begin
    arrHover[1] := 0;
    arrAnimValues[1 ,0] := 0;
end;

procedure TForm1.Shape3MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape3);
end;

procedure TForm1.Shape3MouseEnter(Sender: TObject);
begin
    arrHover[2] := 1;
    arrAnimValues[2 ,0] := 0;
end;

procedure TForm1.Shape3MouseLeave(Sender: TObject);
begin
    arrHover[2] := 0;
    arrAnimValues[2 ,0] := 0;
end;

procedure TForm1.Shape4MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape4);
end;

procedure TForm1.Shape4MouseEnter(Sender: TObject);
begin
    arrHover[3] := 1;
    arrAnimValues[3 ,0] := 0;
end;

procedure TForm1.Shape4MouseLeave(Sender: TObject);
begin
    arrHover[3] := 0;
    arrAnimValues[3, 0] := 0;
    arrAnimValues[3, 1] := 0;

end;

procedure TForm1.Shape4Paint(Sender: TObject);
begin

end;

procedure TForm1.Shape5MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape5);
end;

procedure TForm1.Shape5MouseEnter(Sender: TObject);
begin
    arrHover[4] := 1;
    arrAnimValues[4, 0] := 0;
end;

procedure TForm1.Shape5MouseLeave(Sender: TObject);
begin
    arrHover[4] := 0;
    arrAnimValues[4, 0] := 0;
end;

procedure TForm1.Shape6MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape6);
end;

procedure TForm1.Shape6MouseEnter(Sender: TObject);
begin
    arrHover[5] := 1;
    arrAnimValues[5, 0] := 0;
end;

procedure TForm1.Shape6MouseLeave(Sender: TObject);
begin
    arrHover[5] := 0;
    arrAnimValues[5, 0] := 0;
end;

procedure TForm1.Shape7MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape7);
end;

procedure TForm1.Shape7MouseEnter(Sender: TObject);
begin
    arrHover[6] := 1;
    arrAnimValues[6, 0] := 0;
end;

procedure TForm1.Shape7MouseLeave(Sender: TObject);
begin
    arrHover[6] := 0;
    arrAnimValues[6, 0] := 0;
end;

procedure TForm1.Shape8MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape8);
end;

procedure TForm1.Shape8MouseEnter(Sender: TObject);
begin
    arrHover[7] := 1;
    arrAnimValues[7, 0] := 0;
end;

procedure TForm1.Shape8MouseLeave(Sender: TObject);
begin
    arrHover[7] := 0;
    arrAnimValues[7, 0] := 0;
end;

procedure TForm1.Shape9MouseDown(Sender: TObject; Button: TMouseButton;
    Shift: TShiftState; X, Y: Integer);
begin
    clickTabuleiro(Shape9);
end;

procedure TForm1.Shape9MouseEnter(Sender: TObject);
begin
    arrHover[8] := 1;
    arrAnimValues[8, 0] := 0;
end;

procedure TForm1.Shape9MouseLeave(Sender: TObject);
begin
    arrHover[8] := 0;
    arrAnimValues[8, 0] := 0;
end;

procedure TForm1.Timer1Timer(Sender: TObject);
begin
    if (bool = 0) then
    begin
        //setLength(tabuleiro, 3, 3);
        bool := 1;
    end;

    lScoreP1.Caption := IntToStr(p1Score);
    labelTie.Caption := IntToStr(ties);
    lScoreP2.Caption := IntToStr(p2Score);

    if (arrHover[0] = 1) then
    begin
        if ((Shape1.Height < MaxTop) and (tabuleiro[0, 0] = 0)) then
        begin
            arrAnimValues[0, 0] := arrAnimValues[0, 0] + incrementoHeight;
            Shape1.Height := Shape1.Height + round(arrAnimValues[0, 0]);
            Shape1.Width := Shape1.Width + round(arrAnimValues[0, 0]);
        end;
    end
    else begin
        if (Shape1.Height > TopNormal) then
        begin
            arrAnimValues[0, 0] := arrAnimValues[0, 0] + incrementoHeight;
            Shape1.Height := Shape1.Height - round(arrAnimValues[0, 0]);
            Shape1.Width := Shape1.Width - round(arrAnimValues[0, 0]);
        end;
    end;
    if (arrHover[1] = 1) then
    begin
        if ((Shape2.Height < MaxTop) and (tabuleiro[0, 1] = 0)) then
        begin
            arrAnimValues[1, 0] := arrAnimValues[1, 0] + incrementoHeight;
            Shape2.Height := Shape2.Height + round(arrAnimValues[1, 0]);
            Shape2.Width := Shape2.Width + round(arrAnimValues[1, 0]);
        end;
    end
    else begin
        if (Shape2.Height > TopNormal) then
        begin
            arrAnimValues[1, 0] := arrAnimValues[1, 0] + incrementoHeight;
            Shape2.Height := Shape2.Height - round(arrAnimValues[1, 0]);
            Shape2.Width := Shape2.Width - round(arrAnimValues[1, 0]);
        end;
    end;
    if (arrHover[2] = 1) then
    begin
        if ((Shape3.Height < MaxTop) and (tabuleiro[0, 2] = 0)) then
        begin
            arrAnimValues[2, 0] := arrAnimValues[2, 0] + incrementoHeight;
            Shape3.Height := Shape3.Height + round(arrAnimValues[2, 0]);
            Shape3.Width := Shape3.Width + round(arrAnimValues[2, 0]);
        end;
    end
    else begin
        if (Shape3.Height > TopNormal) then
        begin
            arrAnimValues[2, 0] := arrAnimValues[2, 0] + incrementoHeight;
            Shape3.Height := Shape3.Height - round(arrAnimValues[2, 0]);
            Shape3.Width := Shape3.Width - round(arrAnimValues[2, 0]);
        end;
    end;

    if (arrHover[3] = 1) then
    begin
        if ((Shape4.Height < MaxTop) and (tabuleiro[1, 0] = 0)) then
        begin
            arrAnimValues[3, 0] := arrAnimValues[3, 0] + incrementoHeight;
            Shape4.Height := Shape4.Height + round(arrAnimValues[3, 0]);
            Shape4.Width := Shape4.Width + round(arrAnimValues[3, 0]);
        end;
    end
    else begin
        if (Shape4.Height > TopNormal) then
        begin
            arrAnimValues[3, 0] := arrAnimValues[3, 0] + incrementoHeight;
            Shape4.Height := Shape4.Height - round(arrAnimValues[3, 0]);
            Shape4.Width := Shape4.Width - round(arrAnimValues[3, 0]);
        end;
    end;
    if (arrHover[4] = 1) then
    begin
        if ((Shape5.Height < MaxTop) and (tabuleiro[1, 1] = 0)) then
        begin
            arrAnimValues[4, 0] := arrAnimValues[4, 0] + incrementoHeight;
            Shape5.Height := Shape5.Height + round(arrAnimValues[4, 0]);
            Shape5.Width := Shape5.Width + round(arrAnimValues[4, 0]);
        end;
    end
    else begin
        if (Shape5.Height > TopNormal) then
        begin
            arrAnimValues[4, 0] := arrAnimValues[4, 0] + incrementoHeight;
            Shape5.Height := Shape5.Height - round(arrAnimValues[4, 0]);
            Shape5.Width := Shape5.Width - round(arrAnimValues[4, 0]);
        end;
    end;

    if (arrHover[5] = 1) then
    begin
        if ((Shape6.Height < MaxTop) and (tabuleiro[1, 2] = 0)) then
        begin
            arrAnimValues[5, 0] := arrAnimValues[5, 0] + incrementoHeight;
            Shape6.Height := Shape6.Height + round(arrAnimValues[5, 0]);
            Shape6.Width := Shape6.Width + round(arrAnimValues[5, 0]);
        end;
    end
    else begin
        if (Shape6.Height > TopNormal) then
        begin
            arrAnimValues[5, 0] := arrAnimValues[5, 0] + incrementoHeight;
            Shape6.Height := Shape6.Height - round(arrAnimValues[5, 0]);
            Shape6.Width := Shape6.Width - round(arrAnimValues[5, 0]);
        end;
    end;
    if (arrHover[6] = 1) then
    begin
        if ((Shape7.Height < MaxTop) and (tabuleiro[2, 0] = 0)) then
        begin
            arrAnimValues[6, 0] := arrAnimValues[6, 0] + incrementoHeight;
            Shape7.Height := Shape7.Height + round(arrAnimValues[6, 0]);
            Shape7.Width := Shape7.Width + round(arrAnimValues[6, 0]);
        end;
    end
    else begin
        if (Shape7.Height > TopNormal) then
        begin
            arrAnimValues[6, 0] := arrAnimValues[6, 0] + incrementoHeight;
            Shape7.Height := Shape7.Height - round(arrAnimValues[6, 0]);
            Shape7.Width := Shape7.Width - round(arrAnimValues[6, 0]);
        end;
    end;
    if (arrHover[7] = 1) then
    begin
        if ((Shape8.Height < MaxTop) and (tabuleiro[2, 1] = 0)) then
        begin
            arrAnimValues[7, 0] := arrAnimValues[7, 0] + incrementoHeight;
            Shape8.Height := Shape8.Height + round(arrAnimValues[7, 0]);
            Shape8.Width := Shape8.Width + round(arrAnimValues[7, 0]);
        end;
    end
    else begin
        if (Shape8.Height > TopNormal) then
        begin
            arrAnimValues[7, 0] := arrAnimValues[7, 0] + incrementoHeight;
            Shape8.Height := Shape8.Height - round(arrAnimValues[7, 0]);
            Shape8.Width := Shape8.Width - round(arrAnimValues[7, 0]);
        end;
    end;
    if (arrHover[8] = 1) then
    begin
        if ((Shape9.Height < MaxTop) and (tabuleiro[2, 2] = 0)) then
        begin
            arrAnimValues[8, 0] := arrAnimValues[8, 0] + incrementoHeight;
            Shape9.Height := Shape9.Height + round(arrAnimValues[8, 0]);
            Shape9.Width := Shape9.Width + round(arrAnimValues[8, 0]);
        end;
    end
    else begin
        if (Shape9.Height > TopNormal) then
        begin
            arrAnimValues[8, 0] := arrAnimValues[8, 0] + incrementoHeight;
            Shape9.Height := Shape9.Height - round(arrAnimValues[8, 0]);
            Shape9.Width := Shape9.Width - round(arrAnimValues[8, 0]);
        end;
    end;

end;


end.
