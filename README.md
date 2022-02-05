# My-first-CS-project
CS project for pre-IB CS
package com.company;
import org.w3c.dom.ls.LSOutput;


import java.util.Scanner;
public class Main {

    public static void main(String[] args) {

        Scanner User = new Scanner(System.in);
        System.out.println(" Hi household member! What is your name?");
        String name = User.next();
        char n = name.charAt(0); // stores the first letter of users name as chart that can be used on the clendar

        System.out.println(name + " this is a calendar of this a calendar of housework ( includes cooking, cleaning etc.) for the next two weeks.");
        System.out.println("Your job is to tell me when you are free to do housework");
        //creates the visual calendar
        char[][] Calendar = {{' ', 'M', '|', 'T', '|', 'W', '|', 'T', '|', 'F', '|', 'S', '|', 'S'},
                {'-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'},
                {' ', ' ', '|', ' ', '|', ' ', '|', ' ', '|', ' ', '|', ' ', '|', ' '},
                {'-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'},};

        //calls for function that prints the calendar outside the main
        printCalendar(Calendar);
        // Calls for function that lets user input their workday
        userAvailable(name, Calendar, n);

        System.out.println(" Thank you for your collaboration! Have a pleasant week.");
    }
    //function that prints the calendar
    public static void printCalendar(char[][] Calendar) { // char Calendar in parentheses means that this function uses already existing Calendar char
        for (char[] week : Calendar) {
            for (char w : week) { // char needs to printed symbol by symbol, so this system separates everything
                System.out.print(w);
            }
            System.out.println();
        }
    }

    public static void userAvailable(String name, char[][] Calendar, char n) { // same here; in parentheses functions that have been moved here from elsewhere
        System.out.println(name + " what day would you like to do housework this week");
        updateCalendar(Calendar, n); // calls for the longer function that actually does the job


    }


    public static void updateCalendar(char[][] Calendar, char n) {

        //asks for user to input a day they can work and changes the visual calendar to respond the given reservation
        try (Scanner newDay = new Scanner(System.in)) {
            System.out.println("Enter the day you want to do housework (monday-sunday) in lower cases");
            String day = newDay.next();
           // this system changes empty place to first letter of users name, under the day user has given
            switch (day) {
                case "monday":
                    Calendar[2][2] = n; // numbers mean that symbol is changed in Calendar position [2][2], which is like coordinates but for chars
                    break;
                case "tuesday":
                    Calendar[2][4] = n; // n here is just the first letter of users name, that has been stored earlier. Could also be another symbol, for example X.
                    break;
                case "wednesday":
                    Calendar[2][6] = n;
                    break;
                case "thursday":
                    Calendar[2][8] = n;
                    break;
                case "friday":
                    Calendar[2][10] = n;
                    break;
                case "saturday":
                    Calendar[2][12] = n;
                    break;
                case "sunday":
                    Calendar[2][14] = n;
                    break;
                default:
                    break; }
            printCalendar(Calendar);}
        catch (Exception e) {
            System.out.println(" received exception: " + e);
            System.exit(20); }}
}
