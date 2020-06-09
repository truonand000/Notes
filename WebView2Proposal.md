```c++
interface IWebViewWindowHost
{
    // Intialize and host IWebView
    virtual HRESULT HostWebView() = 0;
    
    // Get pointer to IWebView Instance
    virtual smart_ptr<IWebView> GetIWebView() = 0;
}
_______________________________________________________________

interface IWebView
{
    virtual HRESULT CreateEnviornmentAndInitWebView() = 0;
    virtual HRESULT Navigate(wchar_t * url, 
                     _in_opt_ wchar_t *postData,
                     _in_opt_ wchar_t *httpHeaders) = 0;           
    virtual void ResizeWebview(DWORD width, DWORD height) = 0;
    virtual HWND GetWebViewHWND() = 0;
    virtual HRESULT PostWebMessageAsJSON(LPCWSTR jsonObj) = 0;
    virtual HRESULT PostWebMessageAsString(LPCWSTR message) = 0;   
}

_______________________________________________________________

class SignInWebViewWindowHostWIN32 :
	public IWebViewWindowHost
{
	...
}
_______________________________________________________________

class SignInWebViewWIN32:
	public IWebView
    
{
	...
}

_______________________________________________________________

interface IWebViewFactory
{
public:
	smart_ptr<IWebViewWindowHost> CreateWebViewWindowHost() = 0;
	smart_ptr<IWebView> CreateWebView() = 0;
}

_______________________________________________________________

class SignInWebViewFactoryWIN32 :
	public IWebViewFactory
{
public:
	smart_ptr<IWebViewWindowHost> CreateWebViewWindowHost()
    {
    	return new SignInWebViewWindowHostWIN32();
    }
    
	smart_ptr<IWebView> CreateWebView() override
    {
    	return new SignInWebViewWIN32();
    }
}

```
