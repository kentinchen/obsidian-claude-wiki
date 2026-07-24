一、安装Tesseract-OCR
https://digi.bib.uni-mannheim.de/tesseract/

setx PATH 
setx TESSDATA_PREFIX "C:\Program Files\Tesseract-OCR\tessdata"
tesseract -V

二、安装Tesseract和Pillow
pip install pytesseract
pip install Pillow
D:\Program Files\anconada3\Lib\site-packages\pytesseract

https://www.guwendao.net/user/login.aspx?from=http://so.gushiwen.cn/user/collect.aspx

from PIL import Image, ImageFilter
import pytesseract
def VerifiCode(image_path):
    img = Image.open(image_path)
    # 将图片变成灰色
    img_gray = img.convert('L')
    # 转成黑白图片
    img_black_white = img_gray.point(lambda x: 255 if x > 60 else 0)#自行更改阈值
    img_qucao = img_black_white.filter(ImageFilter.SMOOTH_MORE)
    img_RGB = img_qucao.convert('RGB')
    captcha_text = pytesseract.image_to_string(img_RGB, config='--psm 6')
    # print('识别结果:', captcha_text)
    captcha_text = captcha_text.strip()
    # 输出识别结果
    # print('识别结果:', captcha_text)
    return captcha_text

if __name__=='__main__':
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko)',
               }
    url = 'https://so.gushiwen.cn/user/login.aspx?from=http://so.gushiwen.cn/user/collect.aspx'
    # 创建一个会话对象，以便在多个请求之间共享cookies
    session = requests.Session()
    page_text = session.get(url=url,headers=headers).text
    # 解析验证码图片img史src属性值
    tree = etree.HTML(page_text)
    img_src=tree.xpath( '//*[@id="imgCode"]/@src')[0]
    # print(img_src)
    code_img_src = 'https://so.gushiwen.org'+img_src#
    # print(code_img_src)
    img_data = session.get(url=code_img_src,headers=headers).content#图片是二进制的所以使用content
    # 资验证码图片保存到了本地
    img_path='./验证码/code.jpg'
    with open( img_path,'wb' ) as fp:
        fp.write( img_data)
    img = Image.open(img_path)
    resultVerifiCode=VerifiCode(img_path)#调用工具方法进行验证码自动识别
    plt.figure(figsize=(10, 5))
    plt.subplot(111)
    plt.title('Original Image')
    plt.imshow(img)
    print('识别结果:', resultVerifiCode)
    plt.show()
    #登陆时的表单数据
    data={
    " __VIEWSTATE": "HGoCyqcXPB5M2yaO3lGPOCpWN6KZy4/ZxY6qNiMUsXK5oDoacCt67HVF+5+Og9Vxf3wuJn2XlihWg2khl5akVJRl/R7R/xOwSZ8VpBEUIRyEqB55bk+vxY2K0xzNxVyjEVv0Zn5rDPHQTRvQyrvCL5V4KNc=",
    "__VIEWSTATEGENERATOR": "C93BE1AE",
    "from":"http://so.gushiwen.cn/user/collect.aspx",
    "email":"****",#换成你的账户
    "pwd": "***",#换成你的密码
    "code": resultVerifiCode,
    "denglu": "登录",
    }
    login_url="https://so.gushiwen.cn/user/login.aspx?from=http%3a%2f%2fso.gushiwen.cn%2fuser%2fcollect.aspx"
    login_response = session.post(url=login_url, headers=headers,data=data)
    print(login_response.status_code)
    if login_response.status_code==200:
        login_page_text=login_response.text
        # 检查是否成功登录
        if "我的收藏_古诗文网" in login_page_text:
            print("登录成功")
            with open('../爬取结果/验证码识别登陆/login_page_text.html', 'w', encoding='utf-8') as fp:
                fp.write(login_page_text)
                print("保存成功")
        else:
            print("登录失败")
    # 关闭会话
    session.close()


https://dashboard.capsolver.com/passport/login?redirect=/dashboard


