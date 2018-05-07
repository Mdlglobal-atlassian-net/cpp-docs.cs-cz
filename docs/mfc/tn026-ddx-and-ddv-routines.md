---
title: 'TN026: Rutiny DDX a DDV | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DDX
- DDV
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44a946b21908f45b595056a956c75b234fdbb886
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: Rutiny DDX a DDV
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje výměna dialogových dat (DDX) a architektura ověření (DDV) dat dialogové okno. Také popisuje, jak psát DDX_ nebo DDV_ postupu a jak můžete rozšířit ClassWizard používat vaše rutiny.  
  
## <a name="overview-of-dialog-data-exchange"></a>Přehled výměna dat dialogových oken  
 Všechny funkce dat dialogových oken se provádějí pomocí kódu C++. Neexistují žádné zvláštní prostředky nebo magic makra. Vysílat mechanismu je virtuální funkce, která přepsání v každé třídy dialogového okna, že nemá výměna dialogových dat a ověření. Vždy zjistí následujícím způsobem:  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);
*// call base class  
 *//{{AFX_DATA_MAP(CMyDialog)  
 <data_exchange_function_call>  
 <data_validation_function_call> *//}}AFX_DATA_MAP  
}  
```  
  
 Afx – komentáře speciální formát povolit ClassWizard pro vyhledání a úpravy kódu v rámci této funkce. Kód, který není kompatibilní s ClassWizard musí být umístěny mimo speciální formát komentáře.  
  
 V předchozím příkladu < data_exchange_function_call > je ve formátu:  
  
```  
DDX_Custom(pDX,
    nIDC,
    field);
```  
  
 a < data_validation_function_call > je volitelný a je ve formátu:  
  
```  
DDV_Custom(pDX,
    field, ...);
```  
  
 Více než jednu dvojici DDX_/DDV_ může být součástí každé `DoDataExchange` funkce.  
  
 Seznam všech rutiny výměny dat dialogového okna a rutiny ověřování dat dialogového okna dodávané s knihovnou MFC naleznete v tématu 'afxdd_.h'.  
  
 Právě toho pak bude dat dialogových oken: data členů v **CMyDialog** třídy. Nejsou uložena v struktury nebo nic podobné.  
  
## <a name="notes"></a>Poznámky  
 I když nazýváme soubor "dat dialogových oken", všechny funkce jsou k dispozici v jakékoli třídy odvozené od `CWnd` a nejsou omezeny pouze dialogy.  
  
 Počáteční hodnoty dat se nastavují v standardní C++ konstruktoru, obvykle v bloku s `//{{AFX_DATA_INIT` a `//}}AFX_DATA_INIT` komentáře.  
  
 `CWnd::UpdateData` je operace, která provádí inicializaci a chybě zpracování kolem volání `DoDataExchange`.  
  
 Můžete volat `CWnd::UpdateData` kdykoli provádět výměny dat a ověření. Ve výchozím nastavení `UpdateData`(TRUE) se nazývá ve výchozí `CDialog::OnOK` obslužné rutiny a `UpdateData`(FALSE), se nazývá ve výchozí `CDialog::OnInitDialog`.  
  
 Rutiny DDV_ okamžitě postupujte DDX_ rutiny pro tento *pole*.  
  
## <a name="how-does-it-work"></a>Jak to funguje  
 Není nutné pochopit následující, abyste mohli používat dat dialogových oken. Však pochopení, jak to funguje na pozadí můžete napsat vlastní proceduru exchange nebo ověření.  
  
 `DoDataExchange` – Členská funkce je podobné jako `Serialize` – členská funkce – je zodpovědná za získání nebo nastavení data do nebo z formuláře externí (v tomto případě ovládacích prvků do dialogového okna) z/do data členů v třídě. `pDX` Parametr je kontext provádění výměny dat a je podobná `CArchive` parametru `CObject::Serialize`. `pDX` ( `CDataExchange` Objektu) s se příznak mnohem jako `CArchive` má příznak směru:  
  
-   Pokud **! m_bSaveAndValidate**, pak můžete načíst stav dat do ovládacích prvků.  
  
-   Pokud `m_bSaveAndValidate`, potom nastavit stav data z ovládacích prvků.  
  
 Ověření dochází pouze při `m_bSaveAndValidate` nastavena. Hodnota `m_bSaveAndValidate` je určen podle parametru BOOL `CWnd::UpdateData`.  
  
 Existují tři další zajímavé `CDataExchange` členy:  
  
- `m_pDlgWnd`: Okno (obvykle dialogovém okně) obsahující ovládací prvky. To je k tomu, aby volající globální funkce DDX_ a DDV_ předat 'this' každé rutiny DDX/DDV.  
  
- `PrepareCtrl`, a `PrepareEditCtrl`: připraví ovládací prvek dialogového okna pro data systému exchange. Uloží popisovač tohoto ovládacího prvku nastavení fokusu, pokud se ověřování nezdaří. `PrepareCtrl` slouží pro ovládací prvky nonedit a `PrepareEditCtrl` se používá pro ovládacích prvcích pro úpravy.  
  
- **Selhání**: volat po vyvolání výstrahy uživateli vstupních chyb okno se zprávou. Tato rutina obnoví zaměřuje na poslední ovládací prvek (poslední volání `PrepareCtrl` / `PrepareEditCtrl`) a způsobí výjimku. Tento člen funkci lze volat z DDX_ i DDV_ rutiny.  
  
## <a name="user-extensions"></a>Tato rozšíření  
 Existuje několik způsobů, jak rozšířit výchozí mechanismus DDX/DDV. Můžeš:  
  
-   Přidáte nové datové typy.  
  
 ```  
    CTime 
 ```  
  
-   Přidáte nové postupy exchange (DDX_).  
  
 ```  
    void PASCAL DDX_Time(CDataExchange* pDX,
    int nIDC,
    CTime& tm);

 ```  
  
-   Přidáte nové postupy ověření (DDV_).  
  
 ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX,
    CTime tm,
    BOOL bFuture);
*// make sure time is in the future or past  
 ```  
  
-   Předejte libovolný výrazy postupy ověření.  
  
 ```  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxAge);

 ```  
  
    > [!NOTE]
    >  Takové libovolný výrazy ClassWizard se nedá upravit a proto by měl být přesunut mimo komentáře speciální formátu (/ / {{AFX_DATA_MAP(CMyClass)).  
  
 Máte **DoDialogExchange** – členská funkce patří podmíněné příkazy nebo žádné jiné platné příkazy C++ s míchán výměna a ověření volání funkcí.  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX,
    IDC_SEX,
    m_bFemale);

DDX_Text(pDX,
    IDC_EDIT1,
    m_age);

//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxFemaleAge);

else  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxMaleAge);
```  
  
> [!NOTE]
>  Jako v příkladu nahoře, takový kód ClassWizard se nedá upravit a měli použít pouze mimo speciální formát komentáře.  
  
## <a name="classwizard-support"></a>Podpora ClassWizard  
 ClassWizard podporuje podmnožinu DDX/DDV přizpůsobení tím, že se můžete integrovat vlastní rutiny DDX_ a DDV_ do ClassWizard uživatelské rozhraní. To je výhodné pouze náklady, pokud máte v úmyslu znovu použít konkrétní DDX a DDV rutiny v projektu nebo v mnoha projektů.  
  
 K tomu speciální položky jsou vytvářeny v DDX. CLW (předchozích verzí aplikace Visual C++ uložené tyto informace v APSTUDIO. INI) nebo ve vašem projektu. CLW soubor. Zvláštní údaje, které může být zadán buď v sekci [obecné informace o] vašeho projektu. Soubor CLW nebo v části [ExtraDDX] DDX. CLW soubor v adresáři \Program Files\Microsoft Visual Studio\Visual C ++ \bin. Musíte vytvořit DDX. CLW soubor, pokud ještě neexistuje. Pokud plánujete použít vlastní rutiny DDX_/DDV_ pouze v určitých projektu, přidejte položky do oddílu [obecné informace o] projektu. CLW souboru místo toho. Pokud budete chtít použít rutiny v mnoha projektů, přidejte položky v sekci [ExtraDDX] DDX. CLW.  
  
 Obecný formát tyto speciální položek je:  
  
```  
ExtraDDXCount=n  
```  
  
 kde n je počet řádků ExtraDDX podle  
  
```  
ExtraDDX=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 kde je číslo 1 - n, která určuje, jaký typ DDX v seznamu, který je definovaný.  
  
 Každé pole je oddělená znakem ';'. Dále jsou uvedená pole a jejich účel.  
  
 \<klíče >  
 = seznam jednotlivé znaky, která určuje, pro které ovládací prvky dialogového okna je povolen tento typ proměnné.  
  
 E = úpravy  
  
 C = dvou stavů zaškrtávací políčko  
  
 c = tři stavu zaškrtávací políčko  
  
 R = první přepínač ve skupině  
  
 L = nonsorted seznamu  
  
 l = seřazený seznam  
  
 M = (s úpravy položky) – pole se seznamem  
  
 N = nonsorted rozevíracího seznamu  
  
 n = seřazené rozevíracího seznamu  
  
 1 = Pokud DDX insert musí být přidaní do head seznamu (výchozí je přidat do tail) obecně používá se pro rutiny DDX, které přenášejí vlastnost "Kontrola".  
  
 \<VB klíče >  
 Toto pole se používá pouze v rámci produktu 16bitové pro ovládací prvky VBX (VBX ovládací prvky nejsou podporovány v produktu 32bitová verze)  
  
 \<řádku >  
 Řetězec, který má toto pole se seznamem vlastností (bez uvozovek)  
  
 \<Typ >  
 Jediný identifikátor pro typ pro vydávání v záhlaví souboru. V našem příkladu výše s DDX_Time tento příkaz nastaví na CTime.  
  
 \<VB klíče >  
 Nepoužívá se v této verzi a by měla být prázdná  
  
 \<Shodný >  
 Počáteční hodnota – 0 nebo je prázdný. Pokud je pole prázdné, bude žádné inicializačního řádku napsán v části //{{AFX_DATA_INIT soubor implementace. Prázdná položka se mají použít pro objekty C++ (například `CString`, `CTime`a tak dále), mít konstruktory, které zaručit správné inicializace.  
  
 < DDX_Proc >  
 Jediný identifikátor DDX_ postup. Název funkce C++ musí začínat znakem "DDX_", ale nezadávejte "DDX_" v identifikátoru < DDX_Proc >. V příkladu nahoře bude identifikátor < DDX_Proc > čas. Když ClassWizard zapisuje do souboru implementace ve volání funkce {{AFX_DATA_MAP části, se připojí tento název DDX_, proto přicházejících u DDX_Time.  
  
 \<Komentář >  
 Komentář k zobrazení v dialogovém okně pro proměnnou s Tento DDX. Umístěte text byste chtěli sem a obvykle poskytují něco, který popisuje operaci prováděné na pár DDX/DDV.  
  
 < DDV_Proc >  
 Část DDV položka je nepovinná. Ne všechny rutiny DDX mít odpovídající DDV rutiny. Často je pohodlnější jako nedílné součásti přenos zahrnout fázi ověřování. To je často případ, kdy vaše rutiny DDV nevyžaduje žádné parametry, protože ClassWizard nepodporuje DDV rutiny bez parametrů.  
  
 \<arg >  
 Jediný identifikátor DDV_ postup. Název funkce C++ musí začínat znakem "DDV_", ale nezahrnují "DDX_" v identifikátoru < DDX_Proc >.  
  
 Následuje argumentů DDV 1 nebo 2:  
  
 \<promptX >  
 řetězec umístit nad upravit položku (s & akcelerátoru)  
  
 \<fmtX >  
 znak formátu pro typ arg, jeden z  
  
 d = int  
  
 u = bez znaménka  
  
 D = dlouho int (tj, long)  
  
 U = dlouho bez znaménka (DWORD)  
  
 f = float  
  
 F = double  
  
 s = řetězec  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

