package com.company;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class MyServlet extends HttpServlet {

    private static final String TEMPLATE = "<html>" +
            "<head><title>com.company</title></head>" +
            "<body><h2>%s</h2></body></html>";


    public void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        final String name = req.getParameter("name");
        final String lastname = req.getParameter("lastname");
        final String age = req.getParameter("age");
        final String first_question = req.getParameter("first_question");
        final String second_question = req.getParameter("second_question");

        final String answer1 = req.getParameter("first_question");
        final String st1;
        if ("yes".equals(answer1))
            st1 = String.format(TEMPLATE, "yes");
        else
            st1 = String.format(TEMPLATE, "no");

        final String answer2 = req.getParameter("second_question");
        final String st2;
        if ("yes".equals(answer2))
            st2 = String.format(TEMPLATE, "yes");
        else
            st2 = String.format(TEMPLATE, "no");

        final String r = String.format(TEMPLATE, name + " " + lastname + ": " + age+st1+st2);
        resp.getWriter().println(r);


    }
}
