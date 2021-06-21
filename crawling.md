# dacon 전력사용량 예측 AI 경진대회 - 체감온도 데이터 가져오기

``` python

month = list(range(6,9)) # 필요한 기간 2020년 6월 1일부터 8월 31일까지.
day = list(range(1, 32)) # 날짜는 1일부터 31일까지
time = list(range(0, 24)) # 시간은 0시부터 23시까지 

for m in month:
    for d in day:
        for t in time:
            url = f'http://www.weather.go.kr/weather/observation/currentweather.jsp?auto_man=m&stn=0&type=t99&reg=100&tm=2020.{m}.{d}.{t}%3A00&x=13&y=11'
            try: pd.read_html(url)[0][[(     '지점',                      '지점'), (  '기온(℃)',                    '체감온도')]].to_csv(f'./energy/crawling/weather{m}-{d}-{t}.csv')
                
            except:
                pass


# 6월 31일이 없기때문에 애러가 날거라 생각하고 try, except로 나누어줬지만 6월 31일로 주소를 입력하면 자동으로 7월 1일 페이지로 이동됨. 
# 따라서 6월 31일로 크롤링 된 csv파일들은 별도로 삭제해줌. 

```
