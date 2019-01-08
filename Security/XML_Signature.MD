## SignedInfo

- 전자서명의 대상이 되는 정보를 가져오기 위한 각종 알고리즘과 대상 데이터를 해시(Digest)한 값이 들어있다.
실제로 서명되는 정보로서 서명자의 개인키를 이용해 SignatureValue을 생성한다.

- XML 전자서명은 반드시 정규화 과정을 거친 후 수행되어야 한다. 이유는 다음과 같다.

    - 논리적으로 동일한 문서에 대해 물리적으로 여러 가지 표현이 가능
    - 논리적으로 동일한 XML 문서에 대한 해시 값이 항상 같음을 보장할 수 없음
    - 논리적으로 동일한 XML 문서가 하나의 물리적인 데이터로 변환하는 정규화 필요

- CanonicalizationMethod에는 SignedInfo 원소를 다이제스트하기 전에 그 원소를 정규화할때 사용하는 알고리즘을 지정한다.

- SignatureMethod에는 정규화된 SignedInfo를 SignatureValue로 변환할 때 사용하는 알고리즘이 들어있다.

- Transforms는 자원의 콘텐트가 다이제스트 되기 전에 그에 적용된 처리 단계의 순서화된 목록,  정규화, 인코딩/디코딩(압축포함), XSLT, XPath(소스 문서의 일부분을 누락한 XML 문서 변환 허용)가 들어간다.

- DigestMethod에는 Transforms가 적용된 이후 DigestValue를 만들어 내기 위해 데이터에 적용되는 알고리즘이 들어있다.

- DigestValue에는 데이터객체에 Transform들을 적용한 후 결과로부터 얻은 다이제스트 값이 들어있다. BASE64로 인코딩된다.

## SignatureValue

- SignedInfo에 지정된 알고리즘에 근거하여 SignedInfo를 정규화하고 그 결과에 대해 서명된 디지털 서명의 실제 값이 들어간다. BASE64로 인코딩된다.

## KeyInfo

- 서명 검증에 사용될 공개키(검증키)를 포함