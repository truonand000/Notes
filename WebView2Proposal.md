```c++
interface IWebViewWindowHost
{
    // Trigger initialization of web view and host it within this window.
    virtual HRESULT HostWebView(...) = 0;
    
    // Get pointer to IWebView Instance
    virtual smart_ptr<IWebView> GetIWebView() = 0;
}
_______________________________________________________________

interface IWebView
{
    // Initialize environment (required for each web view instance), 
    // the web view controller, web view instance itself, etc.
    virtual HRESULT CreateEnviornmentAndInitWebView(...) = 0;
    
    // Navigate to provided url. Optional post data and http header params.
    virtual HRESULT Navigate(wchar_t * url, 
                     _in_opt_ wchar_t *postData,
                     _in_opt_ wchar_t *httpHeaders) = 0;
                     
    // Resize Web View bounds
    virtual void ResizeWebview(DWORD width, DWORD height) = 0;
    
    // Post a message to the webpage as a JSON object.
    virtual HRESULT PostWebMessageAsJSON(LPCWSTR jsonObj) = 0;
    
    // Post a message to the webpage as a string.
    virtual HRESULT PostWebMessageAsString(LPCWSTR message) = 0;   
}

_______________________________________________________________

class AbstractWebView
    : public IWebView
    
{
public:
    // Interface Methods
protected:
    // Members like m_webView and m_webViewController are common to all webviews 
    // and are depended upon when registering event handlers, which is the reason 
    // they are protected instead of private.
    smart_ptr<ICoreWebView2> m_webView;
    smart_ptr<ICoreWebView2Controller> m_webViewController;
    
    // Abstract method. Each unique webview will have their own set of event handlers,
    // which will all be registered here.
    virtual void RegisterEventHandlers();
}
_______________________________________________________________

class SignInWebViewWindowHost final:
	public IWebViewWindowHost
{
    // Configure window to fit needs of the web dialog.
}
_______________________________________________________________

class SignInWebView final:
	public AbstractWebView
    
{
	...
protected:

    // Concrete implementation
    void RegisterEventHandlers() override
    {
    	// Register Event Handlers here.
    }
    
private:
    // Other unique members required for webview set up specific to use of the webview case by case.
}

_______________________________________________________________

interface IWebViewFactory
{
public:
	smart_ptr<IWebViewWindowHost> CreateWebViewWindowHost() = 0;
	smart_ptr<IWebView> CreateWebView() = 0;
}

_______________________________________________________________

class SignInWebViewFactory :
	public IWebViewFactory
{
public:
	smart_ptr<IWebViewWindowHost> CreateWebViewWindowHost()
    {
    	return new SignInWebViewWindowHost();
    }
    
	smart_ptr<IWebView> CreateWebView() override
    {
    	return new SignInWebView();
    }
}

```
