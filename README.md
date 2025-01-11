# DS-Algorithm-
This repository contains all the DSA questions that I have done , anyone can take reference


package com.quizportal.controller;

import com.quizportal.dao.UserDAO;
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.IOException;

public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String email = request.getParameter("email");
        String password = request.getParameter("password");

        boolean isValidUser = UserDAO.validateUser(email, password);
        if (isValidUser) {
            HttpSession session = request.getSession();
            session.setAttribute("user", email);
            response.sendRedirect("quiz.jsp");
        } else {
            response.getWriter().println("Invalid credentials.");
        }
    }
}
