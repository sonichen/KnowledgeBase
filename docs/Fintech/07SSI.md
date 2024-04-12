## Digital Identity (e-ID)

### Identity and Authenticity

1. **Biometrics**: Biometric data, such as fingerprints, iris scans, or facial recognition, can uniquely identify an individual. These features are difficult to forge and provide a reliable means of authentication.
2. **Government-Issued IDs**: Official documents like passports, driver’s licenses, and national identification cards contain personal information and a photograph. These serve as proof of identity and are widely accepted for various purposes.
3. **Social Security Numbers (SSNs)**: In some countries, SSNs are used to uniquely identify citizens. However, due to privacy concerns, SSNs should be handled carefully and not shared indiscriminately.
4. **Unique Personal Attributes**: Certain physical or behavioral traits can be used for identification. Examples include voice patterns, handwriting, or even gait recognition.
5. **Digital Signatures**: Digital signatures based on cryptographic keys can verify the authenticity of electronic documents and messages. They link a specific identity to a digital representation.
6. **Personal Identifiable Information (PII)**: PII includes sensitive data that can uniquely identify an individual. Examples include full names, addresses, phone numbers, email addresses, and social security numbers.

Authentication involves proving that you are who you claim to be. It relies on three factors:

1. **Knowledge**: Something you know (e.g., a password or PIN).
2. **Possession**: Something you have (e.g., a physical token or smartphone).
3. **Biometric Features**: Something you are (e.g., fingerprints, face recognition).



An ID document exchange has 3 components:

1. the subject – an individual or an asset

2. the certifier – an organization that notarized documents, i.e. government agencies, universities, accounting firm, …..

3. the inquisitor – an organization conducting enquiries or validation on the subject, i.e. employers, banks, KYC, AML, ….. 

### eID

香港电子身份证（eID）由香港政府信息科技办公室（OGCIO）提供，免费为所有香港居民提供。它允许居民使用单一的数字身份和认证，在线进行政府和商业交易。

以下是关于香港eID的要点：

1. **注册与绑定**：成功注册后，eID将绑定到申请人的个人移动设备上。
2. **生物识别功能**：用户可以利用个人移动设备提供的生物识别功能（包括面部识别、指纹识别等）来验证身份并登录在线服务。
3. **数字签名**：eID还支持根据《电子交易条例》（第553章）的法律支持进行数字签名，用于处理法定文件和程序。

此外，OGCIO将提供三组应用程序编程接口（API）：

- **认证**：用于验证用户身份。
- **表单填写**：用于填写表单。
- **数字签名**：用于支持数字签名。

认证和授权将采用OAuth 2.0协议，用于eID用户、在线服务和eID系统之间的通信。

### Authentication with eID

1. 用户访问在线服务网站并启动eID登录流程。
2. 在线服务将用户重定向到托管在eID系统中的网页。
3. 用户使用eID移动应用程序扫描网页上的QR码。
4. eID系统将用户重定向到在线服务，并附带“授权码”。
5. 在线服务将“授权码”传递给eID系统。
6. eID系统返回包含用户令牌化eID的“访问令牌”，在线服务使用令牌化eID在本地用户数据库中执行用户匹配。

### Digital Signing with eID

1. 用户启动eID数字签名流程（如果用户未经身份验证，则执行“认证”流程的步骤2-6以获取令牌化eID*）。
2. 在线服务将来自要签名的Web表单的哈希值与用户的令牌化eID一起传递给eID系统。
3. 在线服务在eID移动应用程序中显示一个识别码，并邀请用户授权进行数字签名。
4. 确保eID移动应用程序上显示的识别码与在线服务网页上的识别码相同后，用户授权进行数字签名操作。
5. eID系统执行数字签名并返回已签名的哈希和用户的带有公钥的数字证书#给在线服务。
6. 在线服务确认数字签名并向用户显示结果。

## SSI

SSI (Self Sovereignty Identity) 

自主主权身份（Self Sovereign Identity，SSI）

### User-centric model

1. 创建一个称为DID（Decentralized Identifier）的唯一标识符，并将其存储在分布式账本（DLT）/区块链中。

![image-20240412152810318](assets\image-20240412152810318.png)

2. DID与一对公钥和私钥相关联（私钥的某些值的哈希值，即私钥的摘要/数字签名）。

3. 当个人想要在特定交易或服务中证明其身份时，他们可以共享一个与他们的DID相关联的可验证凭证。

4. 可验证凭证由三部分组成：

- Claim声称：我是约翰·史密斯，年龄超过18岁
- Credential凭证：由受信任的机构颁发，包含声明、颁发者的身份、凭证的到期日期等信息
- Proof证明：用于验证凭证的加密算法，例如颁发者和用户的公钥，以及验证者的私钥。

![image-20240412152903114](assets\image-20240412152903114.png)

![image-20240412152916227](assets\image-20240412152916227.png)

### Building Blocks

1. 可验证凭证

   - 包含声明，包括属性（年龄、身高、体重等）、关系（母亲、父亲、雇主、公民身份等）或权利（医疗福利、图书馆特权、会员奖励或法律权利）。

2. 颁发者、持有者和验证者

   - 颁发者是颁发可验证凭证的受信任实体，持有者是持有和管理可验证凭证的个体，验证者是验证持有者身份的实体。

3. 数字钱包

   - 存储可验证凭证和加密密钥的数字化钱包，用于管理个体的身份信息。

4. 数字代理和中心

   - 每个数字钱包都由数字代理“封装”，作为软件守护者，确保只有钱包的控制者（通常是身份所有者）可以访问存储的可验证凭证和加密密钥。

5. 分散式标识符（DID）

   - 用于唯一标识个体的标识符，通常存储在分布式账本（DLT）或区块链中。

6. 分布式账本（DLT）/区块链

   - 用于存储和管理DID以及相关的可验证凭证和加密密钥的技术基础。

7. 治理框架

   - 用于管理和监督SSI生态系统的规则和标准。

### User Case

![image-20240412153009913](assets\image-20240412153009913.png)

![image-20240412153101043](assets\image-20240412153101043.png)

How to establish your genuine identity the first time?

![image-20240412153134893](assets\image-20240412153134893.png)

### 优缺点

自主主权身份（SSI）的优点和缺点如下：

优点：

1. **增强隐私和安全性**：SSI可以减少身份盗窃等安全威胁，因为个体控制自己的个人身份数据。
2. **用户控制个人身份数据**：个体可以自主管理和控制自己的个人身份信息，而不需要依赖中心化的身份管理机构。

缺点：

1. **技术复杂性**：SSI的实施涉及到复杂的加密和分布式技术，可能需要专业的技术团队进行开发和维护。
2. **需要良好的密钥管理/托管/恢复系统**：如果没有有效的密钥管理系统，用户可能会永久丢失他们的身份数据，因此需要建立可靠的密钥管理和恢复机制。
3. **监管准备**：SSI的实施可能需要符合各种监管要求和标准，因此需要确保技术和流程的合规性。
4. **脱机问题**：在设备丢失或损坏的情况下，用户可能无法访问其个人身份数据，因此需要解决离线访问和恢复的问题。



### SSI – DLT

对于自主主权身份（SSI），选择何种类型的分布式账本技术（DLT）取决于其需求和特点。以下是一些常见的DLT类型，可以用于实现SSI：

1. **区块链**：区块链是一种分布式数据库，数据以区块的形式连接在一起，并通过加密技术保证安全性和不可篡改性。区块链可用于存储和验证个人身份数据以及与之相关的验证凭证。
2. **分布式账本技术（DLT）**：除了区块链之外，还有其他形式的DLT，例如图结构或有向无环图（DAG）。这些技术可以提供与区块链类似的分布式特性，但可能在不同的方面具有不同的优势。
3. **去中心化标识协议**：有一些特定的去中心化标识协议，如DID（Decentralized Identifier）和Verifiable Credential等，这些协议为SSI提供了基本的框架和标准，可以在各种DLT上实现。

除了自主主权身份之外，DLT还可以用于许多其他应用。例如：

1. **供应链管理**：DLT可以用于跟踪和管理供应链中的物流和商品流动，从而提高透明度和可追溯性。
2. **金融服务**：DLT可以用于实现分布式支付系统、智能合约和数字资产管理，从而改善金融服务的效率和安全性。
3. **知识产权管理**：DLT可以用于管理和保护知识产权，如版权、专利和商标，确保其真实性和不可篡改性。
4. **投票和选举系统**：DLT可以提供安全、透明和可验证的投票系统，防止选举舞弊和操纵。