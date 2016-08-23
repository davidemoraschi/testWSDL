using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using testWSDL.MicroStrategy;
//using testWSDL.microstrategy;

namespace testWSDL
{
    public partial class Form1 : Form
    {
        private MSTRWSSoapClient mstr = new MSTRWSSoapClient("MSTRWSSoap");
        private MWSConnectInfo ci = new MWSConnectInfo();

        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
             try
            {
                string result = mstr.TestService("eurostrategy.net", "POC - FF01", "Administrator", "PIBdel0,3%");
                txtResult.Text = result;
            }
            catch (Exception soapex)
            {
                //txtResult.Text = soapex.InnerException.ToString();
                throw;
            }            
        }

        private void btnConnect_Click(object sender, EventArgs e)
        {
            try
            {
                ci.AuthMode = EnumMWSAuthMode.MWSStandard;
                ci.Login = "Administrator";
                ci.Password = "PIBdel0,3%";
                ci.ProjectName = "POC - FF01";
                ci.ProjectSource = "IP-10-144-73-168";
                string result = mstr.Connect(null, ci);
                txtResult.Text = result;

            }
            catch (Exception soapex)
            {
                
                throw;
            }
        }

        private void btnExec_Click(object sender, EventArgs e)
        {
            MWSExecuteInfo ei = new MWSExecuteInfo();
            MWSResultsWindow rw = new MWSResultsWindow();
            MWSSoapHeader sh = new MWSSoapHeader();
            //rw.MaxCols = 256;
            //rw.MaxRows = Convert.ToInt32(txtMaxRows.Text);
            //rw.StartCol = 1;
            //rw.StartRow = 1;
            //rw.PopulatePageBy = false;
            //rw.MaxRows = 256;
            MWSExecutionSettings es = new MWSExecutionSettings();
            //es.= 
            ei = mstr.ExecuteReport(null, ci, "Pedidos Clientes", null, null, EnumMWSExecutionFlags.MWSUseDefaultPrompts, null, null, EnumMWSResultFlags.MWSReturnAsHTML, null);
//no:            ei = mstr.ExecuteReport(null, ci, "Pedidos Clientes", null, null, EnumMWSExecutionFlags.MWSUseDefaultPrompts, null, "CustomXMLReportStyle", EnumMWSResultFlags.MWSReturnAsHTML, null);
//png            ei = mstr.ExecuteReport(null, ci, "Pedidos Clientes", null, null, EnumMWSExecutionFlags.MWSUseDefaultPrompts, null, null, EnumMWSResultFlags.MWSGraphImgPNG, null);
            txtResult.Text = ei.ExecuteStatus.ToString();
            webResult.Document.Write(ei.ResultHTML.ToString());
            //ei = mstr.GetReportResults(null, ci, null, "3F04B1024651C365F208A2B29A991B1C", null, EnumMWSExecutionFlags.MWSUseDefaultPrompts, rw, null, EnumMWSResultFlags.MWSReturnAsHTML, es);
            //txtResult.Text = ei.ExecuteStatus.ToString();
        }

        private void btnGetResult_Click(object sender, EventArgs e)
        {
           //MWSExecuteInfo ei = new MWSExecuteInfo();
           //MWSResultsWindow rw = new MWSResultsWindow();           
           //MWSExecutionSettings es = new MWSExecutionSettings();
           //mstr.GetReportResults(null, ci, null, "3F04B1024651C365F208A2B29A991B1C", null, EnumMWSExecutionFlags.MWSUseDefaultPrompts , rw, null, EnumMWSResultFlags.MWSReturnAsHTML , es);
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            webResult.Navigate("about:blank");

        }

        private void btnSimpleExec_Click_1(object sender, EventArgs e)
        {
            MWSSoapHeader sh = new MWSSoapHeader();
            MWSExecuteInfo ei = new MWSExecuteInfo();
            try
            {
                ei = mstr.SimpleExecuteReport(sh, ci, "Pedidos Clientes", null, null);
            }
            catch (Exception ex)
            {
                Console.Write ("");
                throw;
            }

            txtResult.Text = ei.ExecuteStatus.ToString();
        }
    }
}
