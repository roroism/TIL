# TODAY I LEARNED

## Learned

### react-csv

- csv 및 excel 내보내기 기능을 모두 제공하는 이 라이브러리는 다양한 사용자 요구에 대응할 수 있는 유연성을 제공합니다.

#### 설치

`npm install react-csv`

#### import

`import { CSVLink, CSVDownload } from 'react-csv';`

#### 사용

##### CSVLink

- 데이터를 CSV 파일로 내보내는 링크를 생성하려면 CSVLink 컴포넌트를 사용합니다.

`<CSVLink data={data}>Download CSV</CSVLink>`

`<CSVLink data={data} filename={"my-data.csv"} separator={","}>Download CSV</CSVLink>`

##### CSVDownload

- CSVDownload 컴포넌트를 사용하여 클릭 없이 자동으로 CSV 파일을 다운로드할 수도 있습니다.

`<CSVDownload data={data} />`

#### 공식 사이트

`https://github.com/react-csv/react-csv`

