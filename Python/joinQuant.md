##### 获取股票池
    hz = get_index_stocks('000001.XSHG', date=None) #所有上交所股票
    sz = get_index_stocks('399106.XSHE', date=None) #所有深交所股票
    stocks = list(get_all_securities(['stock']).index) #所有沪深股票

##### 过滤停牌股票
    #输入股票池，日期，返回非停牌股票池
    def unpaused(stks,date):
        def ispaused(stk,date):
            var = get_price(stk, start_date=None, end_date=date, frequency='daily', 
                  fields= ['paused'], skip_paused=False, fq='pre', count=1)
            return bool(var['paused'][0])
        return [stk for stk in stks if not ispaused(stk,date)] 

##### 数据API
    get_price(security, start_date=None, end_date=None, frequency='daily', fields=None, skip_paused=False, fq='pre', count=None)