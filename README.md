using System;
using System.Text.RegularExpressions;
using System.Windows.Forms;

namespace YourNamespace
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void btnRegister_Click(object sender, EventArgs e)
        {
            string email = txtEmail.Text;
            string password = txtPassword.Text;
            lblMessage.Text = "";

            // Kiểm tra định dạng email
            var emailPattern = @"^[^@\s]+@[^@\s]+\.[^@\s]+$";
            if (!Regex.IsMatch(email, emailPattern))
            {
                lblMessage.Text = "Email không hợp lệ.";
                lblMessage.ForeColor = System.Drawing.Color.Red;
                return;
            }

            // Kiểm tra mật khẩu
            if (password.Length < 8 || !Regex.IsMatch(password, @"[!@#$%^&*]"))
            {
                lblMessage.Text = "Mật khẩu phải tối thiểu 8 ký tự và có ít nhất 1 ký tự đặc biệt.";
                lblMessage.ForeColor = System.Drawing.Color.Red;
                return;
            }

            // Nếu tất cả hợp lệ
            lblMessage.Text = "Đăng ký thành công!";
            lblMessage.ForeColor = System.Drawing.Color.Green;
        }
    }
}
