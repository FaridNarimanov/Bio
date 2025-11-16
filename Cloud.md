> [!NOTE]
> ## 1. **Bulud arxitekturası**

Bulud arxitekturası – bulud hesablama xidmətlərinin (məsələn, serverlər, yaddaş, şəbəkələr) necə qurulduğunu, idarə olunduğunu və istifadəçilərə çatdırıldığını təsvir edən bir plandır (blueprint). Bu, sadəcə avadanlıq yığımı deyil, bu avadanlığın proqram təminatı vasitəsilə necə idarə olunub paylaşıldığını müəyyən edən komponentlər və onların əlaqəsidir.

Bu arxitekturanın əsas məqsədi, fiziki resursları (serverlər, hard disklər) istifadəçilər üçün çevik, miqyaslana bilən və tələb əsasında əlçatan xidmətlərə çevirməkdir.

### Buludun Təməl Texnikaları: Arxitekturanın "Necə"si

Bir sistemi "bulud" edən iki əsas texniki prinsip var. Mətndə adı çəkilən "abstraksiya" və "orkestrasiya" məhz bunlardır:

1. **Abstraksiya (Mücərrədləşdirmə):**
    
    - **İzahı:** Bu, fiziki resursların (məsələn, konkret bir serverin prosessoru və ya yaddaşı) onların təqdim etdiyi _xidmətdən_ (məsələn, "virtual maşın" və ya "yaddaş bloku") ayrılması prosesidir.
        
    - **Necə İşləyir:** Ən çox **virtuallaşdırma** (virtualization) texnologiyası ilə həyata keçirilir. Bir güclü fiziki server, hipervizor adlı proqram təminatı vasitəsilə bir-birindən xəbərsiz işləyən onlarla kiçik virtual serverə bölünə bilər.
        
    - **Nəticəsi:** Bu, "Resurs Hovuzu" (Resource Pooling) anlayışını yaradır. Artıq müştərilər konkret fiziki serverləri deyil, bu serverlərdən yaradılmış ümumi bir resurs hovuzunu paylaşırlar.
        
2. **Orkestrasiya (Orchestration):**
    
    - **İzahı:** Əgər abstraksiya resursları "parçalayırsa", orkestrasiya bu parçaları idarə edən "beyin"dir. Bu, bütün abstrakt resursları koordinasiya edən, avtomatlaşdıran və idarə edən mürəkkəb proqram təminatı qatıdır.
        
    - **Necə İşləyir:** İstifadəçi bir veb portala daxil olub "mənə 2 CPU və 8 GB RAM-lı bir server lazımdır" düyməsini sıxdıqda, məhz orkestrasiya sistemi arxa planda işə düşür. O, abstrakt resurs hovuzundan həmin resursları tapır, birləşdirir, şəbəkəni konfiqurasiya edir və bir neçə dəqiqəyə istifadəçiyə hazır serveri təqdim edir.
        
    - **Nəticəsi:** Orkestrasiya, "Tələb əsasında özünəxidmət" və "Sürətli elastiklik" kimi xüsusiyyətləri təmin edir.
        

### Buludun 5 Əsas Xarakteristikası (NIST Tərifi)

Bu iki təməl texnika (abstraksiya və orkestrasiya) birləşərək buludun rəsmi olaraq tanınan 5 əsas xüsusiyyətini əmələ gətirir:

1. **Tələb əsasında özünəxidmət (On-demand self-service):** İstifadəçilər provayderin işçisi ilə əlaqə saxlamadan (məsələn, e-poçt yazmadan), bir veb portal vasitəsilə özləri istədikləri resursları (server, yaddaş) anında yarada və silə bilirlər.
    
2. **Geniş şəbəkəyə çıxış (Broad network access):** Bütün resurslar standart şəbəkə protokolları (əsasən internet) vasitəsilə əlçatandır və onlara noutbuk, telefon, planşet kimi müxtəlif cihazlardan daxil olmaq mümkündür.
    
3. **Resurs hovuzu (Resource pooling):** Provayderin bütün fiziki resursları (prosessor, RAM, yaddaş) bir hovuza yığılır və bu hovuzdan müxtəlif müştərilərə xidmət göstərilir. Bu, **çoxistifadəli (multi-tenant)** modeli yaradır. Müştərilər eyni fiziki serveri paylaşa bilər, lakin **izolyasiya** (bir-birinin məlumatını görməməsi) və **ayrılma** (resursların düzgün bölünməsi) sayəsində bundan xəbərsiz olurlar.
    
4. **Sürətli elastiklik (Rapid elasticity):** Arxitektura, istifadəçilərə resursları tələbə görə çox sürətlə artırıb-azaltmağa imkan verir. Məsələn, bir veb-sayta qəfil çoxlu istifadəçi daxil olduqda, sistem avtomatik olaraq server sayını 5-dən 50-yə qaldıra, tələbat azaldıqda isə yenidən 5-ə endirə bilər.
    
5. **Ölçülən xidmət (Measured service):** Bulud sistemi hər bir istifadəçinin nə qədər resurs (məsələn, neçə saat server işlətdiyi və ya neçə GB məlumat saxladığı) istifadə etdiyini dəqiqliklə ölçür və izləyir. Bu, "istifadə etdiyin qədər ödə" (pay-as-you-go) modelinin əsasını təşkil edir.
    

---

## 2. Yerləşdirmə (Deployment) Modelləri: Bulud "Haradadır?"

Bulud arxitekturası, onun harada yerləşdiyinə və kim tərəfindən idarə olunduğuna görə dörd əsas modelə bölünür:

- **Public Cloud (İctimai Bulud):**
    
    - **İzahı:** Resurslar (serverlər, yaddaş) AWS, Google Cloud, Microsoft Azure kimi üçüncü tərəf provayderə məxsusdur və internet üzərindən ictimaiyyətə təqdim olunur.
        
    - **Arxitektura:** Maksimum dərəcədə paylaşılmış, çoxistifadəli (multi-tenant) arxitekturadır.
        
- **Private Cloud (Şəxsi Bulud):**
    
    - **İzahı:** Bulud infrastrukturu yalnız bir təşkilat (məsələn, bir bank) üçün ayrılıb və onun tərəfindən idarə olunur.
        
    - **Arxitektura:** Bu, təşkilatın öz data mərkəzində (on-premises) və ya başqa yerdə ola bilər, lakin resurslar _paylaşılmır_. Tək-istifadəli (single-tenant) arxitekturadır və adətən təhlükəsizlik və nəzarət tələbləri yüksək olduqda seçilir.
        
- **Hybrid Cloud (Hibrid Bulud):**
    
    - **İzahı:** İctimai və şəxsi buludların birləşməsidir. Təşkilatlar texnologiya vasitəsilə bu iki mühit arasında məlumat və tətbiqləri köçürə bilirlər.
        
    - **Arxitektura:** Ən çox yayılmış istifadəsi **"cloud bursting"** (buluda sıçrayış) adlanır. Gündəlik işlər şəxsi buludda (private) gedir, lakin yük qəfil artdıqda (məsələn, "Qara Cümə" endirimləri), əlavə yükü qarşılamaq üçün ictimai buludun (public) resurslarından istifadə olunur.
        
- **Community Cloud (İcma Buludu):**
    
    - **İzahı:** Eyni maraqları (məsələn, təhlükəsizlik standartları, qanunvericilik tələbləri) paylaşan bir neçə təşkilat (məsələn, bir ölkədəki bütün universitetlər və ya bütün banklar) tərəfindən paylaşılan bir bulud infrastrukturudur.
        

---

## 3. Xidmət (Arxitektura) Modelləri: "Məsuliyyət Qatları"

Bulud arxitekturasının ən vacib hissəsi, istifadəçiyə nə qədər nəzarət verildiyini və provayderin nəyə məsul olduğunu müəyyən edən xidmət modelləridir. Bu, adətən bir "stack" (qat) kimi təsvir edilir:

### Infrastructure as a Service (IaaS) - (İnfrastruktur Xidmət Kimi)

- **Nədir:** Bu, ən təməl səviyyədir. Provayder sizə virtual serverlər (hesablama), yaddaş (storage) və şəbəkə kimi fundamental infrastruktur resurslarını təqdim edir.
    
- **Provayderin Məsuliyyəti:** Fiziki serverlərin işləməsi, virtuallaşdırma qatı (hipervizor).
    
- **Sizin Məsuliyyətiniz:** Əməliyyat sistemi (məsələn, Windows/Linux quraşdırmaq, yeniləmək), onun üzərindəki proqramlar (məsələn, verilənlər bazası), tətbiq kodları və məlumatlar.
    
- **Analoji:** Provayder sizə boş bir bina (infrastruktur) verir. İçini necə döşəmək, hansı mebeli qoymaq və təhlükəsizliyini təmin etmək sizin öhdənizdədir.
    

### Platform as a Service (PaaS) - (Platforma Xidmət Kimi)

- **Nədir:** Bu model IaaS üzərində qurulur. Provayder təkcə infrastrukturu deyil, həm də onun üzərindəki əməliyyat sistemini, "middleware"i (məsələn, verilənlər bazası idarəetmə sistemi, veb server) idarə edir.
    
- **Provayderin Məsuliyyəti:** İnfrastruktur + Əməliyyat sistemi (yeniləmələr, təhlükəsizlik yamaları) + İşləmə mühiti (məsələn, Java, Python mühiti).
    
- **Sizin Məsuliyyətiniz:** Yalnız öz tətbiq kodunuzu yazmaq/yükləmək və məlumatlarınızı idarə etmək.
    
- **Analoji:** Provayder sizə tam təchizatlı bir mətbəx (platforma) verir. Ocaq, soyuducu, qablar var. Sizin işiniz sadəcə öz reseptinizlə (kod) yemək bişirməkdir (tətbiq).
    

### Software as a Service (SaaS) - (Proqram Təminatı Xidmət Kimi)

- **Nədir:** Bu, ən yüksək səviyyədir. İstifadəçiyə tamamilə hazır, işlək bir proqram təminatı internet üzərindən (adətən brauzerlə) təqdim olunur.
    
- **Provayderin Məsuliyyəti:** Hər şey – infrastruktur, əməliyyat sistemi, platforma, tətbiqin özü, yeniləmələr, bütün idarəetmə.
    
- **Sizin Məsuliyyətiniz:** Yalnız proqramdan istifadə etmək və öz məlumatlarınızı daxil etmək (və ya sadəcə konfiqurasiya etmək).
    
- **Analoji:** Siz yemək bişirmirsiniz və ya mətbəx icarəyə götürmürsünüz. Sadəcə restorana (SaaS) gəlib hazır yeməyi sifariş edirsiniz (məsələn, Gmail, Office 365, Dropbox istifadə edirsiniz).
    

### Everything as a Service (XaaS)

Bu, yuxarıdakı modellərin məntiqini genişləndirən bir fəlsəfədir. İndi demək olar ki, hər şey (məsələn, Təhlükəsizlik (SecaaS), Verilənlər Bazas (DBaaS), Şəxsiyyət (IDaaS)) bulud üzərindən xidmət kimi təqdim edilə bilər.

> [!NOTE]
> ## 2. **IaaS, PaaS, SaaS təhlükəsizlik riskləri və həlləri**==

Bulud xidmət modellərində (IaaS, PaaS, SaaS) təhlükəsizlik risklərini və həllərini anlamaq üçün əvvəlcə **"Paylaşılan Məsuliyyət Modeli" (Shared Responsibility Model)** anlayışını bilmək vacibdir. Bu model, təhlükəsizliyin hansı hissəsinə görə bulud provayderinin (məsələn, AWS, Azure), hansı hissəsinə görə isə müştərinin (istifadəçi/təşkilat) cavabdeh olduğunu müəyyən edir.

Qayda budur: **Provayder həmişə "buludun özünün" təhlükəsizliyinə cavabdehdir; müştəri isə "buludun içində" olan məlumatlarının, tətbiqlərinin və girişlərinin təhlükəsizliyinə cavabdehdir.**

Məsuliyyət bölgüsü modellərə görə dəyişir:

- **IaaS:** Məsuliyyətin əksəriyyəti müştərinin üzərindədir.
    
- **PaaS:** Məsuliyyət provayder və müştəri arasında bərabərə yaxın bölüşdürülür.
    
- **SaaS:** Məsuliyyətin əksəriyyəti provayderin üzərindədir.
    

Gəlin indi hər modelə bu məsuliyyət bölgüsü çərçivəsində baxaq.

---

### 1. Software as a Service (SaaS) Təhlükəsizliyi

- **Məsuliyyət Modeli:** Burada provayder infrastruktura, platformaya və hətta tətbiqin özünə (proqram koduna) nəzarət edir və onların təhlükəsizliyinə cavabdehdir. İstifadəçi yalnız tətbiqdən istifadəni və ona daxil etdiyi məlumatları idarə edə bilir, lakin tətbiqin işləmə mexanizmini dəyişdirə bilmir. Müştərinin əsas məsuliyyəti **məlumatların idarə edilməsi** və **girişə nəzarətdir**.
    

**Risklər və Həlləri:**

1. **Risk: Məlumat Məxfiliyi və İtkisi**
    
    - **Təsviri:** SaaS provayderi ilə müştəri arasında məlumat paylaşımı (internet üzərindən) zamanı məlumatların oğurlanması (Məlumat Məxfiliyi) və ya sistemdəki boşluqlar səbəbilə məlumatların düzgün qorunmaması, saxlama və nüsxələmə zamanı boşluqlar nəticəsində onların daimi itirilməsi (Məlumat İtkisi) baş verə bilər.
        
    - **Həll Yolları:**
        
        - **Məlumat Şifrələməsi:** Bu, məxfiliyin təminatıdır. Məlumatlar həm **tranzitdə** (yolda, yəni internet üzərindən göndərilərkən SSL/TLS ilə) şifrələnməli, həm də **saxlanma zamanı** (at-rest, yəni provayderin serverlərində) şifrələnməlidir.
            
        - **Məlumat Ehtiyat Nüsxələri:** Məlumat itkisinin qarşısını almaq üçün provayderin (və bəzən müştərinin özünün) məlumatların nizamlı nüsxələnməsi metodlarını tətbiq etməsi şərtdir.
            
2. **Risk: Məlumatların Qanunsuz Çıxarılması (İcazəsiz Giriş)**
    
    - **Təsviri:** SaaS tətbiqlərində zəif kimlik doğrulama (məsələn, sadə şifrələr) və istifadəçi icazə sistemlərinin (avtorizasiya) düzgün konfiqurasiya edilməməsi, hesabların ələ keçirilməsinə və həssas məlumatların oğurlanmasına şərait yaradır.
        
    - **Həll Yolu:**
        
        - **Giriş Nəzarəti (Access Control):** Tətbiq daxilində "ən az imtiyaz prinsipi" (Principle of Least Privilege) tətbiq edilməlidir. Yəni, istifadəçilər üçün dəqiq giriş nəzarəti və yalnız öz işlərini görmələri üçün lazım olan minimum icazələr təyin edilməlidir.
            

---

### 2. Platform as a Service (PaaS) Təhlükəsizliyi

- **Məsuliyyət Modeli:** Provayder infrastrukturun _və_ platformanın (əməliyyat sistemi, verilənlər bazası, işləmə mühiti) təhlükəsizliyinə cavabdehdir. Müştəri isə bu platforma üzərində yazdığı **tətbiq koduna** və **məlumatlara** cavabdehdir. Burada məsuliyyət daha bərabər bölüşdürülür. Müştəri həm də provayderin təqdim etdiyi təhlükəsizlik funksiyalarının (məsələn, firewall qaydaları) necə konfiqurasiya edilməsinə cavabdehdir.
    

**Risklər və Həlləri:**

1. **Risk: Tətbiq Zəiflikləri**
    
    - **Təsviri:** İstifadəçilər (developerlər) tərəfindən PaaS platforması üzərində yazılan kodun özündə (məsələn, SQL Injection, XSS) zəifliklərin olması bulud sisteminin ümumi təhlükəsizliyini poza bilər. Platforma təhlükəsiz olsa belə, onun üzərində işləyən tətbiq zəifdirsə, sistem hücuma məruz qala bilər.
        
    - **Həll Yolu:**
        
        - **Tətbiq Təhlükəsizliyi Yoxlamaları:** Müştəri, yazdığı tətbiq kodunu platformaya yükləməzdən əvvəl ciddi təhlükəsizlik testlərindən (məsələn, statik və dinamik kod analizi - SAST/DAST) keçirməlidir.
            
2. **Risk: API Zəiflikləri**
    
    - **Təsviri:** PaaS xidmətləri adətən bir-biri ilə və kənar xidmətlərlə API-lər (Tətbiq Proqramlaşdırma İnterfeysləri) vasitəsilə əlaqə saxlayır. Bu API-lərin zəifliyi (məsələn, zəif autentifikasiya, sürət məhdudiyyətinin olmaması) kənar hücumlara və məlumat sızmasına yol aça bilər.
        
    - **Həll Yolu:**
        
        - **API Təhlükəsizliyi:** Müştərinin məsuliyyətində olan API-lər düzgün autentifikasiya (məsələn, API açarları, OAuth) və giriş nəzarəti (avtorizasiya) ilə qorunmalıdır.
            
3. **Risk: Kimliklərin Oğurlanması (Zəif Autentifikasiya)**
    
    - **Təsviri:** Zəif autentifikasiya mexanizmləri (tək faktorlu şifrələr) developerlərin və ya administratorların hesablarının ələ keçirilməsinə və nəticədə bütün platformaya icazəsiz girişə səbəb ola bilər.
        
    - **Həll Yolu:**
        
        - **Güclü Kimlik və Giriş İdarəetməsi (IAM):** Platformaya girişi idarə etmək üçün mütləq şəkildə **Çoxfaktorlu Autentifikasiya (MFA)** tətbiq edilməlidir.
            

---

### 3. Infrastructure as a Service (IaaS) Təhlükəsizliyi

- **Məsuliyyət Modeli:** Provayder yalnız fundamental fiziki infrastruktura (serverlər, data mərkəzləri) və virtuallaşdırma qatına (hipervizor) cavabdehdir. Müştəri isə bunun üzərində qurduğu _demək olar ki, hər şeyə_ cavabdehdir: virtual əməliyyat sistemləri (onların yenilənməsi, təhlükəsizliyi), virtual şəbəkələr, tətbiqlər, məlumatlar və s. Bu modeldə **müştərinin üzərinə ən çox məsuliyyət düşür**.
    

**Risklər və Həlləri:**

1. **Risk: Yanlış Konfiqurasiya (Misconfiguration)**
    
    - **Təsviri:** IaaS-də ən böyük risk budur. Müştəriyə çox nəzarət verildiyi üçün səhv etmək şansı da yüksəkdir. Yanlış konfiqurasiya edilmiş bulud resursları (məsələn, internetə tam açıq yaddaş (storage) vedrəsi), təhlükəsizlik üçün quraşdırılmamış açıq şəbəkələr (açıq portlar) və zəif autentifikasiya metodları birbaşa hücuma şərait yaradır.
        
    - **Həll Yolları:**
        
        - **Konfiqurasiya Nəzarəti:** İdarəetmə panellərində təhlükəsizlik qaydaları (policy) tətbiq edilməli, şifrələmə tədbirləri ilə resurslar qorunmalıdır.
            
        - **Şəbəkə Təhlükəsizliyi:** Virtual şəbəkə **Təhlükəsizlik Qruplarının (Security Groups)** və **Firewall-ların** düzgün təyin edilməsi (məsələn, yalnız lazımi portların açıq olması) vacibdir.
            
2. **Risk: Məlumat Sızması (Zəif Şifrələmə)**
    
    - **Təsviri:** Müştəri tərəfindən idarə olunan virtual maşınlar və şəbəkə interfeyslərində zəif şifrələmənin tətbiq edilməsi və ya heç edilməməsi, hücumçuların şəbəkə trafikini dinləyərək məlumatları əldə etməsinə səbəb ola bilər.
        
    - **Həll Yolu:**
        
        - (Konfiqurasiya nəzarətinə daxildir) Müştəri məlumatların həm saxlanmada, həm də tranzitdə (məsələn, virtual serverlər arasında) şifrələnməsini özü təmin etməlidir.
            
3. **Risk: DDoS Hücumları**
    
    - **Təsviri:** Provayderlər adətən infrastruktur səviyyəsində DDoS qoruması təmin etsə də, hücumçular birbaşa müştərinin virtual serverlərinə və saxlama sistemlərinə (müştərinin IP ünvanlarına) yüksək trafik göndərərək DDoS hücumları ilə təzyiq göstərə bilər.
        
    - **Həll Yolları:**
        
        - **DDoS Qarşısının Alınması:** Provayderin təqdim etdiyi xüsusi DDoS qoruma xidmətlərindən və düzgün konfiqurasiya edilmiş Firewall-lardan istifadə edilməlidir.
            
        - **Monitorinq və Müdaxilə Aşkarlanması:** Hər hansı anormal fəaliyyəti və təhdidləri erkən aşkarlamaq üçün **IDPS (Müdaxilə Aşkarlama və Qarşısının Alınması Sistemləri)** kimi monitorinq sistemlərinin istifadəsi vacibdir.


> [!NOTE]
> ## 3. **Bulud təhlükəsizliyinin elementləri**==

Bulud təhlükəsizliyinin "elementləri" dedikdə, adətən bulud mühitini qorumaq üçün istifadə olunan nəzarət mexanizmləri (məsələn, IAM, şəbəkə təhlükəsizliyi, şifrələmə) nəzərdə tutulur. 

2008-ci ildə "Gartner" analitik şirkəti "Bulud Texnologiyalarının Təhlükəsizlik Risklərinin Qiymətləndirilməsi" adlı mühüm bir hesabat dərc etdi. Bulud texnologiyasının hələ yeni olduğu o dövrdə, bu hesabat müəssisələrin buluda keçid zamanı mütləq təhlil etməli olduğu 7 əsas təhlükəsizlik məsələsini (narahatlığını) müəyyənləşdirdi. Bu 7 məsələ bu gün də aktualdır və müasir bulud təhlükəsizliyi siyasətlərinin təməlini təşkil edir:

### 1. İmtiyazlı İstifadəçi Girişi (Privileged User Access)

- **Problem (Risk):** Müəssisələr məxfi məlumatlarını bulud provayderinə həvalə etdikdə, məlumatlar fiziki olaraq müəssisədən xaricə çıxır və onlar məlumat üzərindəki fiziki nəzarəti itirirlər. Əsas risk odur ki, təkcə müştərinin öz administratorları deyil, həm də bulud provayderinin öz əməkdaşları (məsələn, sistemi idarə edən mühəndislər) bu məlumatlara nəzəri olaraq giriş əldə edə bilər.
    
- **Həll Yolu (Müasir Nəzarət):** Bu riskə qarşı "onların məlumat üzərində hansı səviyyədə girişi var" və "girişləri necə idarə olunur" kimi suallara cavab olaraq provayderlər güclü **Kimlik və Giriş İdarəetməsi (IAM)** siyasətləri, "Sıfır Güvən" (Zero Trust) modelləri və audit jurnalları təqdim edir. Ən yüksək nəzarət üçün müştərilər öz məlumatlarını provayderin belə oxuya bilmədiyi **müştəri tərəfindən idarə olunan açarlarla** şifrələyə bilərlər (Client-Side Encryption).
    

### 2. Normativ Uyğunluq (Regulatory Compliance)

- **Problem (Risk):** Xidmət provayderləri məlumatları buludda saxlaya və idarə edə bilər, lakin qanun qarşısında (məsələn, bankçılıq, səhiyyə və ya GDPR qaydaları) məlumatların bütövlüyü və məxfiliyinə görə **nəticə etibarilə cavabdehlik müəssisənin (müştərinin) öz üzərində qalır.**
    
- **Həll Yolu (Müasir Nəzarət):** Müştərilər bu cavabdehliyi yerinə yetirmək üçün təhlükəsizlik sertifikatları (məsələn, ISO 27001, SOC 2, PCI-DSS) olan və xarici audit firmaları tərəfindən müntəzəm yoxlamalar keçirən provayderləri seçməlidirlər. Provayderlər bu audit hesabatlarını müştərilərə təqdim edərək öz mühitlərinin uyğunluğunu sübut edirlər.
    

### 3. Məlumatın Yerləşməsi (Data Location)

- **Problem (Risk):** Provayderlər məlumatları dünyanın müxtəlif yerlərində yerləşən data mərkəzlərində saxlayır. Standart halda, istifadəçilər məlumatlarının məhz hansı ölkə və ya regionda saxlandığını bilməyə bilər. Bu, xüsusilə Avropa Birliyinin GDPR kimi məlumat suverenliyi qanunları olan regionlarda ciddi hüquqi problem yaradır.
    
- **Həll Yolu (Müasir Nəzarət):** Müasir bulud provayderləri bu problemi həll etmək üçün **"Regionlar" (Regions)** konsepsiyasını təqdim edir. Xüsusi uyğunluq tələbləri olduqda, müştəri xidmət yaradarkən məlumatların saxlanacağı konkret coğrafi regionu (məsələn, "Almaniya, Frankfurt" və ya "ABŞ, Virciniya") özü seçir və provayder bu məlumatların həmin regiondan kənara çıxarılmayacağına zəmanət verir.
    

### 4. Məlumatların Məntiqi Ayrılması (Data Segregation)

- **Problem (Risk):** Bulud hesablama "çoxistifadəli" (multi-tenant), yəni paylaşılan xidmət kimi işləyir. Bu o deməkdir ki, bir neçə fərqli müştərinin məlumatları (və ya virtual maşınları) eyni fiziki server üzərində yerləşə bilər. Bu, bir istifadəçinin məlumatlarının digərinə sızması kimi kritik bir təhlükəsizlik riski yaradır.
    
- **Həll Yolu (Müasir Nəzarət):** Provayderlər fərqli istifadəçilərin məlumatlarını ayırmaq üçün güclü məntiqi mexanizmlər tətbiq edirlər. Əsas mexanizm **hipervizor vasitəsilə virtuallaşdırma izolyasiyasıdır** (bir virtual maşının digərinin yaddaşını oxuya bilməməsi). Əlavə təbəqə olaraq **şifrələmə** (data-at-rest) tətbiq olunur ki, hətta fiziki diskə giriş olsa belə, məlumatlar oxunmasın. Provayderlər bu texnikaların ekspertlər tərəfindən sınaqdan keçirildiyini təmin etməlidirlər.
    

### 5. Bərpa (Recovery)

- **Problem (Risk):** İstənilən sistemdə nasazlıq (məsələn, data mərkəzinin yanması, elektrik kəsilməsi) baş verə bilər. Müştəri bilməlidir ki, belə bir fəlakət halında onun məlumatlarının aqibəti nə olacaq və xidmətlər nə qədər vaxta bərpa olunacaq (RTO/RPO).
    
- **Həll Yolu (Müasir Nəzarət):** Tam bərpa (Disaster Recovery) üçün provayderlər məlumat və tətbiq infrastrukturunu bir neçə fərqli fiziki məkanda (məsələn, eyni region daxilində fərqli **"Əlçatanlıq Zonaları" - Availability Zones**). Müştəri öz xidmətini qurarkən bu zonalardan istifadə edərək sistemini dayanıqlı (highly available) konfiqurasiya edə bilər.
    

### 6. Tədqiqat Dəstəyi (Investigative Support)

- **Problem (Risk):** Bulud mühitində qanunsuz fəaliyyətin (məsələn, haker hücumu və ya daxili pozuntu) araşdırılması çətin ola bilər. Səbəb odur ki, məlumatlar davamlı dəyişən (dinamik) nodlar üzərində təşkil oluna bilər və log faylları bir neçə istifadəçinin fəaliyyəti ilə qarışa bilər.
    
- **Həll Yolu (Müasir Nəzarət):** Müasir provayderlər bu problemi hərtərəfli **loqlama (logging) və monitorinq** xidmətləri ilə həll edir (məsələn, AWS CloudTrail, Azure Monitor). Bu sistemlər mühitdə baş verən _hər bir_ hərəkəti (kim, nə vaxt, hansı IP-dən, nə etdi) dəyişdirilə bilməyən jurnallarda saxlayır. Bu, tədqiqat (forensics) aparmaq üçün kritik əhəmiyyət daşıyır. Müştərilər həmçinin provayderdən müəyyən növ araşdırmalarda dəstək verməyə dair müqavilə öhdəliyi tələb edə bilərlər.
    

### 7. Uzunmüddətli Davamlılıq (Long-term Viability)

- **Problem (Risk):** Bu, texniki deyil, daha çox biznes riskidir. Bulud xidmət provayderinin fəaliyyətini dayandırması (iflas) və ya başqa bir şirkət tərəfindən satın alınması baş verə bilər. Belə halda, müştərinin məlumatlarının saxlanması və əlçatanlığı ilə bağlı ciddi suallar yaranır: "Məlumatlarım mövcud qalacaqmı? Onları necə geri ala biləcəm?"
    
- **Həll Yolu (Müasir Nəzarət):** Bu, **"Çıxış Strategiyası" (Exit Strategy)** adlanır. Təşkilatlar müqavilə bağlamadan öncə provayderdən onların məlumatlarını saxlama müddəti, xidmət ləğv edildikdən sonra məlumatların necə və hansı formatda geri qaytarılacağı (data portability) barədə aydın və detallı məlumat tələb etməlidirlər.
    

Gördüyünüz kimi, Gartner-in 2008-ci ildə qaldırdığı bu 7 məsələ, bu günün bulud təhlükəsizlik arxitekturasının təməl prinsiplərinə çevrilib.


> [!NOTE]
> ## **4. Bulud Kub Modeli**

Bulud Kub Modeli bulud hesablama mühitlərini təsnifləşdirmək və onların təhlükəsizlik aspektlərini anlamaq üçün bir konseptual çərçivədir. Modelin əsas məqsədi, təhlükəsiz bulud hesablamaları üçün **standartlaşdırmaya əsas yaratmaq** olmuşdur.

### Modelin Yaranma Səbəbi: "De-Perimetrizasiya" Problemi

Model ilk olaraq **"de-perimetrizasiya" (de-perimeterization)** adlanan mühüm bir təhlükəsizlik problemini həll etmək üçün hazırlanmışdır.

- **Ənənəvi Model:** Klassik təhlükəsizlik yanaşması "qala və xəndək" modelinə əsaslanırdı. Burada şəbəkənin aydın sərhədləri (perimetri) var idi: "daxili" (etibarlı zona) və "xarici" (etibarsız zona, internet).
    
- **Problem:** Lakin bulud texnologiyaları, mobil işçilər və təşkilatlar arasında əməkdaşlıq (məsələn, partnyor şirkətlərə daxili sistemlərə giriş verilməsi) bu sərhədlərin pozulmasına səbəb oldu. Artıq "daxili" və "xarici" kimi məhdud baxış bucaqları təhlükəsizliyi təmin etmək üçün kifayət deyildi.
    

### Modelin Əsas Fəlsəfəsi

Bulud Kub Modeli göstərir ki, bulud təhlükəsizliyi artıq yalnız sistemin "daxili" və ya "xarici" olması ilə qiymətləndirilməməlidir. Təhlükəsizlik risklərini tam anlamaq üçün başqa vacib amillər də təsir edir. Model, təhlükəsizlik siyasəti hazırlayarkən bu amilləri nəzərə almağı təklif edir, məsələn:

- **Məlumatın Yeri:** Məlumatlar tam olaraq istehlakçının (müştərinin) öz şəbəkə sərhədləri daxilindədir, yoxsa kənardadır?
    
- **İdarəetmə Məsuliyyəti:** Bulud infrastrukturunun idarə edilməsinə kim cavabdehdir (müştərinin özü, yoxsa kənar provayder)?
    
- **Giriş Hüquqları:** Bulud resurslarına və məlumatlara giriş hüquqları kimdədir və bu girişlər necə idarə olunur?
    

### Bulud Kub Modelinin Əsas Məqsədləri

Bu model, buludun istənilən formalaşma növlərində (yəni yuxarıdakı amillərin müxtəlif kombinasiyalarında) təhlükəsizlik məsələlərini anlamağa böyük töhfə verir. Modelin qurulmasının əsas məqsədləri aşağıdakılardır:

1. **Buludun Müxtəlif Formalaşmalarını Göstərmək:** Buludun fərqli növlərini (məsələn, daxili şəxsi bulud, kənardan idarə olunan ictimai bulud və s.) təsnifləşdirmək.
    
2. **Xüsusiyyətləri Vurğulamaq:** Hər bir bulud formalaşmasının (növünün) əsas texniki və idarəetmə xüsusiyyətlərini müəyyən etmək.
    
3. **Risk/Fayda Analizi:** Hər bir bulud formasının spesifik üstünlüklərini (məsələn, çeviklik) və daşıdığı riskləri (məsələn, nəzarətin itirilməsi) nümayiş etdirmək.
    
4. **Ənənəvi Yanaşmanı Dəyərləndirmək:** Model həmçinin göstərir ki, ənənəvi, bulud əsaslı olmayan yanaşma (tamamilə daxili data mərkəz) tamamilə köhnəlməyib və müəyyən həssas biznes funksiyalarının icrası üçün hələ də ən uyğun seçim ola bilər.
    
5. **Yol Xəritəsi Təqdim Etmək:** Bulud mühitini daha təhlükəsiz etmək və bu sahədə daha ətraflı araşdırmalar aparmaq üçün bir yol xəritəsi (metodologiya) təqdim etmək.


> [!NOTE]
> ## **5.Zero Trust modeli**==

Bu cavab iki əsas hissədən ibarətdir: birincisi "Zero Trust" (Sıfır Etibar) modelinin nə olduğunu, ikincisi isə bu modelin hansı təhlükəsizlik siyasətləri vasitəsilə tətbiq edildiyini izah edir.

### 1. Zero Trust (Sıfır Etibar) Modeli Nədir?

"Sıfır Etibar" (Zero Trust) ənənəvi "qala və xəndək" (içəridəkilərə etibar et, çöldəkilərə etibar etmə) modelini rədd edən müasir bir təhlükəsizlik strategiyasıdır.

Bu model, bulud mühitlərində **"heç kimə etibar etmə, hər zaman yoxla"** prinsipinə əsaslanır. Fərqi yoxdur istifadəçi şəbəkə daxilindədir, yoxsa xaricində – hər bir istifadəçi və cihaz şübhəli kimi qəbul olunur. Onlara yalnız autentifikasiyadan (kimlik doğrulamadan) keçdikdən sonra resurslara giriş əldə etməsinə imkan verilir və bu etibar daimi olmur, onlar hər zaman yenidən yoxlanılır.

#### Zero Trust Modelinin Əsas Prinsipləri:

Bu modeli həyata keçirmək üçün dörd əsas prinsipə əməl olunur:

1. **Minimum İcazə Prinsipi (Least Privilege):** İstifadəçilərə və sistemlərə yalnız öz işlərini yerinə yetirmək üçün lazım olan ən minimal hüquqlar və giriş icazələri verilir.
    
2. **Kontekst Yönümlü Giriş Nəzarəti:** Kimlik doğrulama zamanı sadəcə şifrəyə deyil, həm də **kontekstə** baxılır. Buraya cihazın yeri, vaxtı, hansı resurslara giriş istədiyi, cihazın təhlükəsizlik vəziyyəti (məsələn, antivirusu yenidirmi?) və s. daxildir.
    
3. **Davranışın Davamlı Monitorinqi və Yenidən Yoxlanılması:** Şəbəkəyə daxil olduqdan sonra belə, istifadəçilər və cihazlar davamlı olaraq izlənilir. Əgər bir istifadəçi qeyri-adi bir davranış (məsələn, gecə saat 3-də həssas faylları yükləmək) göstərərsə, onun etibar statusu ləğv edilə və ya yenidən kimlik doğrulaması tələb oluna bilər.
    
4. **Sıx Audit və Loqlama (Logging):** Hər bir fəaliyyət (uğurlu və uğursuz girişlər, fayl müraciətləri) ətraflı şəkildə izlənilir (loqlanır) ki, hər hansı anomaliya və potensial risklər vaxtında aşkar edilsin.
    

---

### 2. Təhlükəsizlik Siyasəti: Zero Trust Modelinin Tətbiq Vasitəsi

Bəs "Zero Trust" kimi bir model və ya strategiya bir təşkilatda real olaraq necə tətbiq edilir? Cavab: **Təhlükəsizlik Siyasətləri** vasitəsilə.

Təhlükəsizlik siyasəti – sistemdə etibarlı təhlükəsizlik tədbirlərinin (məsələn, Zero Trust prinsiplərinin) necə həyata keçirilməsini tənzimləyən rəsmi sənədlər toplusudur.

- Bu siyasətlər **rəhbərlik tərəfindən** müəyyən olunur (məsələn, "Biz Zero Trust modelinə keçirik").
    
- Onlara əsasən texniki **standartlar, qaydalar və prosedurlar** hazırlanır (məsələn, "Hər kəs MFA istifadə etməlidir" qaydası).
    

Bulud təhlükəsizliyi strategiyası da məhz bu sistem, proqram təminatı və informasiya siyasətlərini əhatə edir. Bulud provayderi (və müştəri öz məsuliyyət sahəsində) bu siyasətlərə uyğun şəkildə təhlükəsizlik qaydalarını təmin etməlidir.

#### Təhlükəsizlik Siyasətlərinin Növləri

Bu siyasətlər məqsədlərinə görə əsasən dörd növə bölünür:

1. **İdarəetmə Siyasəti (Management Policy):**
    
    - **Nədir:** Təşkilatın təhlükəsizlik hədəflərini və prinsiplərini müəyyən edən yüksək səviyyəli sənəddir. Rəhbərlik tərəfindən müəyyən edilən ümumi prinsipləri əhatə edir.
        
    - **Nümunə:** "Bütün məlumatlar həssaslıq dərəcəsinə görə təsnifləşdirilməlidir", "Backup tezliyi 24 saatdan bir olmalıdır", "Bulud yerləşdirmə növü olaraq Hibrid Buluda üstünlük verilir".
        
2. **Normativ Siyasət (Regulatory Policy):**
    
    - **Nədir:** Təşkilatın öz istəyindən asılı olmayan, xarici qüvvələr (dövlət, sənaye qurumları) tərəfindən tələb olunan məcburi qaydalardır.
        
    - **Nümunə:** Banklar üçün Mərkəzi Bankın tələbləri, səhiyyə məlumatları üçün HIPAA və ya Avropa məlumatları üçün GDPR qaydaları. Bu siyasətlər hüquqi və tənzimləyici tələblərə uyğunluğu təmin edir.
        
3. **Məsləhətverici Siyasət (Advisory Policy):**
    
    - **Nədir:** Məcburi deyil, lakin təhlükəsizliyi artırmaq üçün tövsiyə olunan ən yaxşı təcrübələrdir (best practices).
        
    - **Nümunə:** "Şifrələrinizi hər 90 gündən bir dəyişməyiniz tövsiyə olunur" və ya "Xarici audit şirkəti tərəfindən dövri təhlükəsizlik yoxlamalarının aparılması məsləhətdir".
        
4. **Məlumatlandırıcı Siyasət (Informative Policy):**
    
    - **Nədir:** Təhlükəsizlik məsələləri barədə daxili (işçilər) və xarici tərəfləri (müştərilər, partnyorlar) məlumatlandırmağa yönələn sənədlərdir.
        
    - **Nümunə:** İşçilər üçün "Fişinq hücumlarını necə tanımaq olar?" təlimatı və ya "Şirkətin məlumat məxfiliyi bəyannaməsi".
        

Beləliklə, təşkilat rəhbərliyi "İdarəetmə Siyasəti"ndə Zero Trust-ı hədəf olaraq təyin edir, "Normativ Siyasət"lər bunu məcbur edə bilər və "Məlumatlandırıcı Siyasət"lər işçilərə bunun səbəbini izah edir.
