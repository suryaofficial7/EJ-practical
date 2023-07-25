# Enterprise java Servlet  COOKIES
# PRactical 2B (COOKIES in JAVA SERVLETS ....)
## S.Surya -COOKIES BASED PROGRAM >>>>
### some imp topics 
1. cookies declaration - >     Cookie c1 = new Cookie("valueName","Value");
   * example Cookie c1 = new Cookie("userView","1");
2. GET ALL COOKIES -> request.getCookie();
3. SETTING VALUE TO THE BROWSER : -> request.addCookie(cookie name); eX: request.addCookie(c1);
4. SET EXPIRESES --> c1.setMaxAge(in Sececonds);
```
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/JSP_Servlet/Servlet.java to edit this template
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;


/**
 *
 * @author surya
 */
public class cook extends HttpServlet {

    /**
     * Processes requests for both HTTP <code>GET</code> and <code>POST</code>
     * methods.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
            /* TODO output your page here. You may use following sample code. */
            out.println("<!DOCTYPE html>");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Servlet cook</title>");            
            out.println("</head>");
            out.println("<body>");
            
                            Cookie []rc = request.getCookies();

            if(request.getCookies()==null){
Cookie c1 = new Cookie("view","1");
c1.setMaxAge(5);
 out.println(c1.getValue());
response.addCookie(c1);
            }
            else{
            out.println(rc[0].getValue());
                        int x = Integer.parseInt(rc[0].getValue());
x++;
//rc[0].setMaxAge(10);
            rc[0].setValue(""+x);
            response.addCookie(rc[0]);
            rc[0].setMaxAge(5);

            }
            
            out.println("</body>");
            out.println("</html>");
        
    }

    // <editor-fold defaultstate="collapsed" desc="HttpServlet methods. Click on the + sign on the left to edit the code.">
    /**
     * Handles the HTTP <code>GET</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Handles the HTTP <code>POST</code> method.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }

    /**
     * Returns a short description of the servlet.
     *
     * @return a String containing servlet description
     */
    @Override
    public String getServletInfo() {
        return "Short description";
    }// </editor-fold>

}


```  
