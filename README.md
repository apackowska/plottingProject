# plottingProject
from graphics import GraphWin, Point, Rectangle, Circle, Text, Image
import matplotlib.pyplot as plt
import pandas as pd


def first(win):
    message = Text(Point(250, 50), "Do you want a Univariate or bivariate plot? Click the button")
    message.draw(win)
    univariate = Text(Point(150, 150), "Univariate")
    univariate.draw(win)
    UniCircle = Circle(center=Point(150, 200), radius=20)
    UniCircle.setFill("red")
    UniCircle.draw(win)
    bivariate = Text(Point(350, 150), "Bivariate")
    bivariate.draw(win)
    BivCircle = Circle(center=Point(350, 200), radius=20)
    BivCircle.setFill("red")
    BivCircle.draw(win)
    button = Rectangle(Point(25, 450), Point(100, 400))
    button.draw(win)
    Text(Point(60, 425), "Quit").draw(win)

def quit_button(win):
    notClicked = True
    while notClicked:
        pt = win.getMouse()
        if 25 <= pt.getX() <= 100 and 400 <= pt.getY() <= 450:
            notClicked = False
            win.close()



def univariate_window(win):
    for item in win.items[:]:
        item.undraw()
    win.update()

    message = Text(Point(250, 50), "Choose a variable and a type of graph")
    message.draw(win)

    ageButton = Rectangle(Point(120, 180), Point(180, 220))
    ageButton.setFill("green")
    ageButton.draw(win)
    age = Text(Point(150, 200), "Age")
    age.draw(win)

    resultButton = Rectangle(Point(220, 180), Point(280, 220))
    resultButton.setFill("green")
    resultButton.draw(win)
    result = Text(Point(250, 200), "Result")
    result.draw(win)

    genderButton = Rectangle(Point(320, 180), Point(380, 220))
    genderButton.setFill("green")
    genderButton.draw(win)
    gender = Text(Point(350, 200), "Gender")
    gender.draw(win)

    barPlotButton = Rectangle(Point(120, 330), Point(180, 370))
    barPlotButton.setFill("yellow")
    barPlotButton.draw(win)
    barPlot = Text(Point(150, 350), "Bar Plot")
    barPlot.draw(win)

    pieChartButton = Rectangle(Point(220, 330), Point(280, 370))
    pieChartButton.setFill("yellow")
    pieChartButton.draw(win)
    pieChart = Text(Point(250, 350), "Pie Chart")
    pieChart.draw(win)

    boxPlotButton = Rectangle(Point(320, 330), Point(380, 370))
    boxPlotButton.setFill("yellow")
    boxPlotButton.draw(win)
    boxPlot = Text(Point(350, 350), "Box Plot")
    boxPlot.draw(win)

    QuitUnivariateButton = Rectangle(Point(25, 450), Point(100, 400))
    QuitUnivariateButton.setFill("red")
    QuitUnivariateButton.draw(win)
    Text(Point(60, 425), "QUIT").draw(win)

    return ageButton, resultButton, genderButton, barPlotButton, pieChartButton, boxPlotButton

def bivariate_window(win):
    for item in win.items[:]:
        item.undraw()
    win.update()

    message = Text(Point(250, 50), "Choose two variables and a type of graph")
    message.draw(win)

    var1Button = Rectangle(Point(120, 180), Point(180, 220))
    var1Button.setFill("green")
    var1Button.draw(win)
    var1 = Text(Point(150, 200), "payor_group")
    var1.draw(win)

    var2Button = Rectangle(Point(220, 180), Point(280, 220))
    var2Button.setFill("green")
    var2Button.draw(win)
    var2 = Text(Point(250, 200), "ct_result")
    var2.draw(win)

    var3Button = Rectangle(Point(320, 180), Point(380, 220))
    var3Button.setFill("green")
    var3Button.draw(win)
    var3 = Text(Point(350, 200), "age")
    var3.draw(win)

    var4Button = Rectangle(Point(120, 230), Point(180, 270))
    var4Button.setFill("green")
    var4Button.draw(win)
    var4 = Text(Point(150, 250), "gender")
    var4.draw(win)

    var5Button = Rectangle(Point(220, 230), Point(280, 270))
    var5Button.setFill("green")
    var5Button.draw(win)
    var5 = Text(Point(250, 250), "rec_ver_tat")
    var5.draw(win)

    var6Button = Rectangle(Point(320, 230), Point(380, 270))
    var6Button.setFill("green")
    var6Button.draw(win)
    var6 = Text(Point(350, 250), "col_rec_tat")
    var6.draw(win)

    graph1Button = Rectangle(Point(120, 330), Point(180, 370))
    graph1Button.setFill("yellow")
    graph1Button.draw(win)
    graph1 = Text(Point(150, 350), "Scatter plot")
    graph1.draw(win)

    graph2Button = Rectangle(Point(220, 330), Point(280, 370))
    graph2Button.setFill("yellow")
    graph2Button.draw(win)
    graph2 = Text(Point(250, 350), "Bar Graph")
    graph2.draw(win)

    graph3Button = Rectangle(Point(320, 330), Point(380, 370))
    graph3Button.setFill("yellow")
    graph3Button.draw(win)
    graph3 = Text(Point(350, 350), "Correlation Graph")
    graph3.draw(win)

    QuitBivariateButton = Rectangle(Point(25, 450), Point(100, 400))
    QuitBivariateButton.setFill("red")
    QuitBivariateButton.draw(win)
    Text(Point(60, 425), "QUIT").draw(win)

    return var1Button, var2Button, var3Button, graph1Button, graph2Button, graph3Button


def option_buttons(win, data):
    my_click = win.getMouse()

    if 100 <= my_click.getX() <= 200 and 180 <= my_click.getY() <= 220:
        ageButton, resultButton, genderButton, barPlotButton, pieChartButton, boxPlotButton = univariate_window(win)
        variable = None
        while True:
            click = win.getMouse()

            if 120 <= click.getX() <= 180 and 180 <= click.getY() <= 220:
                variable = 'age'
            elif 220 <= click.getX() <= 280 and 180 <= click.getY() <= 220:
                variable = 'result'
            elif 320 <= click.getX() <= 380 and 180 <= click.getY() <= 220:
                variable = 'gender'
            elif 120 <= click.getX() <= 180 and 330 <= click.getY() <= 370:
                graph_type = 'Bar Plot'
                if variable:
                    plot_and_display_uni(win, data, variable, graph_type)

            elif 220 <= click.getX() <= 280 and 330 <= click.getY() <= 370:
                graph_type = 'Pie Chart'
                if variable:
                    plot_and_display_uni(win, data, variable, graph_type)

            elif 320 <= click.getX() <= 380 and 330 <= click.getY() <= 370:
                graph_type = 'Box Plot'
                if variable:
                    plot_and_display_uni(win, data, variable, graph_type)

            elif 25 <= click.getX() <= 100 and 400 <= click.getY() <= 450:
                win.close()
                break


    elif 300 <= my_click.getX() <= 400 and 180 <= my_click.getY() <= 220:
        var1Button, var2Button, var3Button, graph1Button, graph2Button, graph3Button = bivariate_window(win)
        variable1 = None
        variable2 = None
        graph_type = None

        while True:
            click = win.getMouse()

            if 120 <= click.getX() <= 180 and 180 <= click.getY() <= 220:
                if not variable1:
                    variable1 = 'payor_group'
                elif not variable2:
                    variable2 = 'payor_group'
            elif 220 <= click.getX() <= 280 and 180 <= click.getY() <= 220:
                if not variable1:
                    variable1 = 'ct_result'
                elif not variable2:
                    variable2 = 'ct_result'
            elif 320 <= click.getX() <= 380 and 180 <= click.getY() <= 220:
                if not variable1:
                    variable1 = 'age'
                elif not variable2:
                    variable2 = 'age'
            elif 120 <= click.getX() <= 180 and 230 <= click.getY() <= 270:
                if not variable1:
                    variable1 = 'gender'
                elif not variable2:
                    variable2 = 'gender'
            elif 220 <= click.getX() <= 280 and 230 <= click.getY() <= 270:
                if not variable1:
                    variable1 = 'rec_ver_tat'
                elif not variable2:
                    variable2 = 'rec_ver_tat'
            elif 320 <= click.getX() <= 380 and 230 <= click.getY() <= 270:
                if not variable1:
                    variable1 = 'col_rec_tat'
                elif not variable2:
                    variable2 = 'col_rec_tat'
            elif 120 <= click.getX() <= 180 and 330 <= click.getY() <= 370:
                graph_type = 'Scatter Plot'
                if variable1 and variable2:
                    plot_and_display_biv(win, data, variable1, variable2, graph_type)
            elif 220 <= click.getX() <= 280 and 330 <= click.getY() <= 370:
                graph_type = 'Bar Graph'
                if variable1 and variable2:
                    plot_and_display_biv(win, data, variable1, variable2, graph_type)
            elif 320 <= click.getX() <= 380 and 330 <= click.getY() <= 370:
                graph_type = 'Correlation Graph'
                if variable1 and variable2:
                    plot_and_display_biv(win, data, variable1, variable2, graph_type)
            elif 25 <= click.getX() <= 100 and 400 <= click.getY() <= 450:

                win.close()
                break

            if variable1 and variable2 and graph_type:
                output = Text(Point(250, 400), f"You chose '{variable1}' and '{variable2}' and it will be displayed as '{graph_type}'")
                output.draw(win)
                break

    elif 25 <= my_click.getX() <= 100 and 400 <= my_click.getY() <= 450:
        # Close window if the user clicks on the exit button
        win.close()


def plot_and_display_uni(win, data, variable, graph_type):
    plt.clf()
    if graph_type == 'Bar Plot':
        plt.hist(data[variable])
        plt.title(f'Bar Plot for {variable}')

    elif graph_type == 'Pie Chart':
        if data[variable].dtype == 'O':
            counts = data[variable].value_counts()
            plt.pie(counts, labels=counts.index, autopct='%1.1f%%')
            plt.title(f'Pie Chart for {variable}')
        else:
            error_text(win, "Can't create a Pie Chart for numeric data.")
            return

    elif graph_type == 'Box Plot':
        if data[variable].dtype == 'O':
            error_text(win, "Can't create a Box Plot for categorical data.")
            return
        plt.figure(figsize=(6, 6))
        plt.boxplot(data[variable], vert=False, showfliers=False)
        plt.xlabel(variable)
        plt.title(f'Boxplot for {variable}')

    plt.xlabel(variable)
    plt.ylabel('Frequency')
    plt.ioff()
    plt.savefig('plot.png', format='png', dpi=75)
    img = Image(Point(700, 250), 'plot.png')
    img.draw(win)
    win.update()
    win.getMouse()
    img.undraw()


def plot_and_display_biv(win, data, variable1, variable2, graph_type):
    if graph_type == 'Scatter Plot':
        if data[variable1].dtype == 'O' or data[variable2].dtype == 'O':
            error_text(win, "Can't create a Scatter Plot for categorical data.")
            return
        plt.scatter(data[variable1], data[variable2])
        plt.title(f'Scatter Plot for {variable1} and {variable2}')

    elif graph_type == 'Bar Graph':
        if data[variable1].dtype == 'O':
            cross_tab = pd.crosstab(data[variable1], data[variable2])

            cross_tab.plot(kind='bar', stacked=True)
            plt.legend()
            plt.show()

    elif graph_type == 'Correlation Graph':
        numeric_data = data.apply(lambda x: pd.to_numeric(x, errors='coerce'))
        correlation_matrix = numeric_data[[variable1, variable2]].corr()
        plt.matshow(correlation_matrix)
        plt.title(f'Correlation Graph for {variable1} and {variable2}')
        plt.colorbar()  # Add color bar for correlation values

    plt.xlabel(variable1)
    plt.ylabel(variable2)
    plt.ioff()
    plt.savefig('plot.png', format='png', dpi=75)
    img = Image(Point(700, 250), 'plot.png')
    img.draw(win)
    win.update()
    win.getMouse()
    img.undraw()


def error_text(win, message):
    text = Text(Point(250,400), message)
    text.draw(win)
    win.update()
    win.getMouse()
    text.undraw()

def main():
    data = pd.read_csv('/Users/ania/Desktop/covid_testing.csv')
    win = GraphWin("Programming Project", 950, 500)
    first(win)
    option_buttons(win, data)
    win.getMouse()
    win.close()

main()
