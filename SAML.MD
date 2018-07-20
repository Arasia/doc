# SAML

    SP-User-IdP 구성
    Redirect를 이용한 SP-IdP 통신
    인증 정보를 Assertion에 담아 통신
    Profile - binding - protocol - assertion 구조


## 관련 링크
[위키 SAML](https://ko.wikipedia.org/wiki/SAML)  
[위키 SAML2.0](https://en.wikipedia.org/wiki/SAML_2.0)  
[SAML 기술개요](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html)  
[Example SAMl Assertions](https://developer.salesforce.com/docs/atlas.en-us.sso.meta/sso/sso_saml_assertion_examples.htm)  
[SAML doc](http://saml.xml.org/wiki/saml-wiki-knowledgebase)  
[SAML SSO](http://rakisis.tistory.com/2)


- ## Assertion

        [필수옵션]
        version : Assertion의 버전 정보  
        ID : Assertion의 식별자 정보  
        IssueInstant : 발행 시간(UTC 시간)  
        <Issuer> : 발행 기관 정보  
        <Statement> : 인증 정보  
        <AuthnStatement> : 인증문  
        <AuthzDecisionStatement> : 허가 결정 진술서(어설션에 의한 액세스 요청이 증거를 기반으로 지정된 권한을 얻음을  증명하는 명령문)  
        <AttributeStatement> : 속성 명령문 

        [선택옵션]
        <ds:Signature> : 무결성을 보호하고 발급자를 인증하는 XML 서명  
        <Subject> : Assertion의 대상  
            <Conditions> : Assertion의 유효성을 위한 정보  
            <NotBefore>, <NotOnOrAfter> : 유효성에 대한 기간 설정  
            <OneTimeUse> : 재사용 불가 설정  
            <Audience> :  응답 받는 주소  
        <Advice> : 추가적인 Assertion 정보


    * ### AuthnStatement  

            AuthnInstant [필수] : 인증된 시간  
            SessionIndex : 식별한 주체와 인증기관 간의 특정 세션 색인을 지정  
            SessionNotOnOrAfter : 세션의 유효상한시간  
            <SubjectLocality> : 어설션 대상이 인증된 시스템의 주소  
            <AuthnContext> : 인증 기관에서 사용하는 구문

        * #### AuthnContext  
                 <AuthnContextClassRef> : <AuthnContextDecl> 또는 <AuthnContextDeclRef>를 기술하는 인증문맥 클래스를 식별하는 URI 참조  
                <AuthnContextDecl> or <AuthnContextDeclRef> : 값에 의해 제공되는 인증 컨텍스트 선언 또는 그러한 선언을 식별하는 URI 참조  
                <AuthenticatingAuthority>

                   
- ## Protocol

    ### Status Response Type

        ID [필수]
        Version [필수]
        IssueInstant [필수]
        <Status> [필수]
        InResponseTo
        Destination
        Consent
        <saml : Issuer>
        <ds:Signature>
        <Extensions>

    ### Request Abstract Type  
    
        ID [필수]
        Version [필수]
        IssueInstant [필수]
        Destination
        Consent
        <saml:Issuer>
        <ds:Signature>
        <Extensions>

    * ### Authentication Request

        + #### AuthnRequest : Request Abstract Type 상속받음
                <saml:Subject> : 결과 어설션을 확인할 수 있는 방법 또는 대상
                <NameIDPolicy> : 요청한 Subject의 이름 식별자에 대한 제약 조건
                <saml:Conditions> 
                <RequestedAuthnContext> : 인증문 요구사항 지정
                <Scoping> : 신뢰하는 IdP 집합을 지정
                ForceAuthn : 보안 컨텍스트에 의존하지 않고 직접 발표자를 인증 T/F
                IsPassive : 요청자의 사용자 인터페이스를 시각적으로 제어하고 눈에 띄는 방식으로 발표자와 상호 작용 T/F (T일시 시각적 방식 X, default F)
                AssertionConsumerServiceIndex
                AssertionConsumerServiceURL : Response 메시지가 반환되는 위치와 binding조건 설정
                ProtocolBinding
                AttributeConsumingServiceIndex
                ProviderName

    * ### Assertion Query and Request
    * ### Artifact Resolution
    * ### NameIdenfitier management
    * ### Single Logout
    * ### Name Identifier Mapping


- ## Binding

    * ### HTTP Redirect
    * ### HTTP Post
    * ### HTTP Artifact
    * ### SAML SOAP


- ## Profile


- ## Metadata

    * ### EntityDescriptor
            entityID [필수]
            ID
            validUntil
            cacheDuration : 메타데이터를 cache하는 최소 기간
            <ds:Signature>
            <Extensions>
            <SPSSODescriptor>, <IDPDescriptor> … [1개 이상]
            <Organization>
            <ContactPerson>
            <AdditionalMetadataLocation>
    
    * ### RoleDescriptor
            ID
            ValidUntil
            CacheDuration
            ProtocolSupportEnumeration [필수]
            errorURL
            <ds:Signature>
            <Extensions>
            <KeyDescriptor>
            <Organization>
            <ContactPerson>

        * #### SSODescriptorType : RoleDescriptor 상속받음
                <ArtifactResolutionService>
                <SingleLogoutService>*
                <ManageNameIDService>*
                <NameIDFormat>
            
            * #### IDPSSODescriptor : SSODescriptorType 상속받음
                    WantAuthnRequestsSigned
                    <SingleSignOnService> [1개이상]*
                    <NameIDMappingService>*
                    <AssertionIDRequestService>*
                    <AttributeProfile>
                    <saml:Attribute>
            
            * #### SPSSODescriptor : SSODescriptortype 상속받음
                    AuthnRequestsSigned
                    WantAssertionsSigned
                    <AssertionConsumerService>
                    <AttributeConsumingService>
            
            * ##### EndPointType : 바인딩 타입과 해당 타입에 대한 URI명시 (*표시)
                    Binding [필수] : 바인딩 옵션
                    Location [필수] : 바인딩 URI
                    ResponseLocation
            
            * ##### NameID Format
                    Unspecified : 특정 되지 않음
                    Email Address : 이메일 주소를 통한 식별
                    persistent : 영구적인 식별자임을 의미
                    transient : 일시적인 식별자임을 의미






