# MCP 服务器 API 文档

本文档详细介绍了 MCP 服务器提供的所有 API 工具。

## 股票市场工具 (`stock_market.py`)

### `get_historical_k_data`

获取中国A股股票的历史K线（OHLCV）数据。

**参数:**

*   `code` (str): Baostock 格式的股票代码 (例如, 'sh.600000', 'sz.000001')。
*   `start_date` (str): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (str): 结束日期，格式为 'YYYY-MM-DD'。
*   `frequency` (str, optional): 数据频率。默认为 'd' (日线)。
*   `adjust_flag` (str, optional): 复权标志。默认为 '3' (不复权)。
*   `fields` (Optional[List[str]], optional): 要检索的特定数据字段。
*   `limit` (int, optional): 返回的最大行数。默认为 250。
*   `format` (str, optional): 输出格式。默认为 'markdown'。

**示例:**

```
get_historical_k_data(code='sh.600000', start_date='2024-01-01', end_date='2024-01-31')
```

### `get_stock_basic_info`

获取给定中国A股股票的基本信息。

**参数:**

*   `code` (str): Baostock 格式的股票代码。
*   `fields` (Optional[List[str]], optional): 要检索的特定数据字段。
*   `format` (str, optional): 输出格式。默认为 'markdown'。

**示例:**

```
get_stock_basic_info(code='sh.600000')
```

### `get_dividend_data`

获取给定股票代码和年份的股息信息。

**参数:**

*   `code` (str): Baostock 格式的股票代码。
*   `year` (str): 查询年份 (例如, '2023')。
*   `year_type` (str, optional): 年份类型。默认为 'report'。
*   `limit` (int, optional): 返回的最大行数。默认为 250。
*   `format` (str, optional): 输出格式。默认为 'markdown'。

**示例:**

```
get_dividend_data(code='sh.600000', year='2023')
```

### `get_adjust_factor_data`

获取给定股票代码和日期范围的复权因子数据。

**参数:**

*   `code` (str): Baostock 格式的股票代码。
*   `start_date` (str): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (str): 结束日期，格式为 'YYYY-MM-DD'。
*   `limit` (int, optional): 返回的最大行数。默认为 250。
*   `format` (str, optional): 输出格式。默认为 'markdown'。

**示例:**

```
get_adjust_factor_data(code='sh.600000', start_date='2024-01-01', end_date='2024-01-31')
```

## 分析工具 (`analysis.py`)

### `get_stock_analysis`

提供基于数据的股票分析报告，而非投资建议。

**参数:**

*   `code` (str): 股票代码，如'sh.600000'。
*   `analysis_type` (str, optional): 分析类型，可选'fundamental'(基本面)、'technical'(技术面)或'comprehensive'(综合)。

**示例:**

```
get_stock_analysis(code='sh.600000', analysis_type='comprehensive')
```

## 日期实用工具 (`date_utils.py`)

### `get_latest_trading_date`

获取截至今日的最新交易日。

**示例:**

```
get_latest_trading_date()
```

### `get_market_analysis_timeframe`

获取根据当前日历上下文调整的市场分析时间范围标签。

**参数:**

*   `period` (str, optional): 'recent' (默认), 'quarter', 'half_year', 'year' 之一。

**示例:**

```
get_market_analysis_timeframe(period='quarter')
```

### `is_trading_day`

检查给定日期是否为交易日。

**参数:**

*   `date` (str): 'YYYY-MM-DD' 格式的日期。

**示例:**

```
is_trading_day(date='2025-01-03')
```

### `previous_trading_day`

获取给定日期之前的上一个交易日。

**参数:**

*   `date` (str): 'YYYY-MM-DD' 格式的日期。

**示例:**

```
previous_trading_day(date='2025-01-06')
```

### `next_trading_day`

获取给定日期之后的下一个交易日。

**参数:**

*   `date` (str): 'YYYY-MM-DD' 格式的日期。

**示例:**

```
next_trading_day(date='2025-01-06')
```

## 财务报告工具 (`financial_reports.py`)

### `get_profit_data`

获取股票的季度盈利能力数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_profit_data(code='sh.600000', year='2023', quarter=4)
```

### `get_operation_data`

获取股票的季度运营能力数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_operation_data(code='sh.600000', year='2023', quarter=4)
```

### `get_growth_data`

获取股票的季度成长能力数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_growth_data(code='sh.600000', year='2023', quarter=4)
```

### `get_balance_data`

获取股票的季度资产负债/偿债能力数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_balance_data(code='sh.600000', year='2023', quarter=4)
```

### `get_cash_flow_data`

获取股票的季度现金流量数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_cash_flow_data(code='sh.600000', year='2023', quarter=4)
```

### `get_dupont_data`

获取股票的季度杜邦分析数据。

**参数:**

*   `code` (str): 股票代码。
*   `year` (str): 4位数字的年份。
*   `quarter` (int): 季度 (1, 2, 3, 或 4)。

**示例:**

```
get_dupont_data(code='sh.600000', year='2023', quarter=4)
```

### `get_performance_express_report`

获取指定日期范围内股票的业绩快报。

**参数:**

*   `code` (str): 股票代码。
*   `start_date` (str): 开始日期 (报告发布/更新)，格式为 'YYYY-MM-DD'。
*   `end_date` (str): 结束日期 (报告发布/更新)，格式为 'YYYY-MM-DD'。

**示例:**

```
get_performance_express_report(code='sh.600000', start_date='2024-01-01', end_date='2024-03-31')
```

### `get_forecast_report`

获取指定日期范围内股票的业绩预告。

**参数:**

*   `code` (str): 股票代码。
*   `start_date` (str): 开始日期 (报告发布/更新)，格式为 'YYYY-MM-DD'。
*   `end_date` (str): 结束日期 (报告发布/更新)，格式为 'YYYY-MM-DD'。

**示例:**

```
get_forecast_report(code='sh.600000', start_date='2024-01-01', end_date='2024-03-31')
```

## 辅助工具 (`helpers.py`)

### `normalize_stock_code`

将股票代码规范化为 Baostock 格式。

**参数:**

*   `code` (str): 原始股票代码 (例如, '600000', '000001.SZ', 'sh600000')。

**示例:**

```
normalize_stock_code(code='600000')
```

### `list_tool_constants`

列出工具参数的有效常量。

**参数:**

*   `kind` (Optional[str], optional): 可选过滤器: 'frequency' | 'adjust_flag' | 'year_type' | 'index'。如果为 None，则显示所有。

**示例:**

```
list_tool_constants(kind='frequency')
```

## 指数工具 (`indices.py`)

### `get_stock_industry`

获取特定股票或指定日期所有股票的行业分类。

**参数:**

*   `code` (Optional[str], optional): Baostock 格式的可选股票代码。如果为 None，则返回所有股票。
*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_stock_industry(code='sh.600000')
```

### `get_sz50_stocks`

获取给定日期的上证50指数成分股。

**参数:**

*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_sz50_stocks()
```

### `get_hs300_stocks`

获取给定日期的沪深300指数成分股。

**参数:**

*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_hs300_stocks()
```

### `get_zz500_stocks`

获取给定日期的中证500指数成分股。

**参数:**

*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_zz500_stocks()
```

### `get_index_constituents`

获取主要指数的成分股。

**参数:**

*   `index` (str): 'hs300' (沪深300), 'sz50' (上证50), 'zz500' (中证500) 之一。
*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_index_constituents(index='hs300')
```

### `list_industries`

列出给定日期的不同行业。

**参数:**

*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
list_industries()
```

### `get_industry_members`

获取在指定日期属于给定行业的所有股票。

**参数:**

*   `industry` (str): 要筛选的精确行业名称。
*   `date` (Optional[str], optional): 可选的 'YYYY-MM-DD' 格式日期。如果为 None，则使用最新的可用日期。

**示例:**

```
get_industry_members(industry='银行')
```

## 宏观经济工具 (`macroeconomic.py`)

### `get_deposit_rate_data`

获取指定日期范围内的存款基准利率。

**参数:**

*   `start_date` (Optional[str], optional): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (Optional[str], optional): 结束日期，格式为 'YYYY-MM-DD'。

**示例:**

```
get_deposit_rate_data(start_date='2020-01-01', end_date='2024-01-01')
```

### `get_loan_rate_data`

获取指定日期范围内的贷款基准利率。

**参数:**

*   `start_date` (Optional[str], optional): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (Optional[str], optional): 结束日期，格式为 'YYYY-MM-DD'。

**示例:**

```
get_loan_rate_data(start_date='2020-01-01', end_date='2024-01-01')
```

### `get_required_reserve_ratio_data`

获取指定日期范围内的存款准备金率数据。

**参数:**

*   `start_date` (Optional[str], optional): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (Optional[str], optional): 结束日期，格式为 'YYYY-MM-DD'。
*   `year_type` (str, optional): 日期筛选的年份类型。'0' 为公告日期 (默认)，'1' 为生效日期。

**示例:**

```
get_required_reserve_ratio_data(start_date='2020-01-01', end_date='2024-01-01')
```

### `get_money_supply_data_month`

获取指定日期范围内的月度货币供应量数据。

**参数:**

*   `start_date` (Optional[str], optional): 开始日期，格式为 'YYYY-MM'。
*   `end_date` (Optional[str], optional): 结束日期，格式为 'YYYY-MM'。

**示例:**

```
get_money_supply_data_month(start_date='2023-01', end_date='2024-01')
```

### `get_money_supply_data_year`

获取指定日期范围内的年度货币供应量数据。

**参数:**

*   `start_date` (Optional[str], optional): 开始年份，格式为 'YYYY'。
*   `end_date` (Optional[str], optional): 结束年份，格式为 'YYYY'。

**示例:**

```
get_money_supply_data_year(start_date='2020', end_date='2023')
```

## 市场概览工具 (`market_overview.py`)

### `get_trade_dates`

获取指定范围内的交易日期。

**参数:**

*   `start_date` (Optional[str], optional): 开始日期，格式为 'YYYY-MM-DD'。
*   `end_date` (Optional[str], optional): 结束日期，格式为 'YYYY-MM-DD'。

**示例:**

```
get_trade_dates(start_date='2024-01-01', end_date='2024-01-31')
```

### `get_all_stock`

获取指定日期的所有股票（A股和指数）列表及其交易状态。

**参数:**

*   `date` (Optional[str], optional): 日期，格式为 'YYYY-MM-DD'。

**示例:**

```
get_all_stock(date='2024-01-05')
```

### `search_stocks`

按代码子串搜索指定日期的股票。

**参数:**

*   `keyword` (str): 股票代码中要匹配的子串。
*   `date` (Optional[str], optional): 'YYYY-MM-DD' 格式的日期。

**示例:**

```
search_stocks(keyword='600')
```

### `get_suspensions`

列出指定日期停牌的股票。

**参数:**

*   `date` (Optional[str], optional): 'YYYY-MM-DD' 格式的日期。

**示例:**

```
get_suspensions(date='2024-01-05')
```
