---
title: 'TN033: DLL verze knihovny MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: 4bfc60e20a073dd34945b91dd48ba82cdf4ab9f3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767779"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: DLL verze knihovny MFC

Tato poznámka popisuje, jak můžete pomocí knihovny MFCxx.DLL a MFCxxD.DLL (kde x je číslo verze knihovny MFC) sdílené knihovny DLL s aplikací knihovny MFC a MFC – rozšiřující knihovny DLL. Další informace o běžných knihovnách MFC DLL, naleznete v tématu [pomocí knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Tato technická Poznámka popisuje tři aspekty knihovny DLL. Poslední dva jsou pro pokročilejší uživatele:

- [Jak vytvářet rozšíření knihovny MFC DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Jak vytvářet aplikace knihovny MFC, která používá knihovnu DLL verze knihovny MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Sdílení knihovny DLL MFC jsou implementovány.](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Pokud vás zajímá vytváření knihovny DLL pomocí knihovny MFC, který lze použít s aplikacemi non-MFC (tomu se říká běžné knihovny MFC DLL), podívejte se na [Technická poznámka 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Přehled knihovny MFCxx.DLL podpory: Terminologie a soubory

**Běžné knihovny MFC DLL**: Běžné knihovny MFC DLL použijete k sestavení samostatné knihovny DLL pomocí některé z třídy knihovny MFC. Rozhraní hranice aplikace/DLL jsou rozhraní "C" a klientská aplikace nemusí být aplikace knihovny MFC.

Toto je verze podpora DLL, které jsou podporované ve verzi 1.0 knihovny MFC. Je popsána v [Technická poznámka 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) a ukázce MFC Advanced Concepts [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> Od verze Visual C++ verze 4.0 termín **USRDLL** je zastaralá a nahradila ji běžné knihovny MFC DLL, která staticky propojuje ke knihovně MFC. Může také vytvořit standardní knihovny MFC DLL, která dynamicky propojuje ke knihovně MFC.

MFC 3.0 (a vyšší) podporuje běžných knihovnách MFC DLL se všechny nové funkce, včetně tříd OLE a databáze.

**AFXDLL**: To se také označuje jako sdílenou verzi knihovny MFC. Toto je novou podporu knihovny DLL do MFC 2.0. Samotné knihovny MFC je v řadě knihoven DLL (popsaných níže) a klientská aplikace nebo knihovny DLL dynamicky propojuje knihovny DLL, které jsou potřeba. Rozhraní hranice aplikace/DLL jsou C++/MFC třídy rozhraní. Klientská aplikace musí být aplikace knihovny MFC. Tento atribut podporuje všechny funkce MFC 3.0 (výjimka: UNICODE není podporován pro databázové třídy).

> [!NOTE]
> Od verze Visual C++ verze 4.0 tento druh knihovny DLL se označuje jako "Rozšiřující knihovny DLL."

Tato poznámka bude používat knihovny MFCxx.DLL jako reference pro celou nastavit knihovnu MFC DLL, která zahrnuje:

- Ladění: MFCxxD.DLL (kombinace) a MFCSxxD.LIB (static).

- Verze: (Kombinace) knihovny MFCxx.DLL a MFCSxx.LIB (static).

- Ladění Unicode: MFCxxUD.DLL (kombinace) a MFCSxxD.LIB (static).

- Verze Unicode: MFCxxU.DLL (kombinace) a MFCSxxU.LIB (static).

> [!NOTE]
> MFCSxx [U] [D]. Lib – knihovny se používají ve spojení s MFC sdílené knihovny DLL. Tyto knihovny obsahovat kód, který se musí do aplikace nebo knihovna DLL staticky propojené.

Odkazy na aplikace na odpovídající importovat knihovny:

- Ladění: MFCxxD.LIB

- Verze: MFCxx.LIB

- Ladění Unicode: MFCxxUD.LIB

- Verze Unicode: MFCxxU.LIB

"Knihovny MFC rozšíření DLL" je postavené na knihovny MFCxx.DLL knihovny DLL (a/nebo jiné knihovny MFC sdílených knihoven DLL). Tady architektura součástí knihovny MFC aktivuje. Pokud užitečné třídu odvodit z třídy knihovny MFC nebo vytvářet další knihovny MFC jako toolkit, je možné je umístit v knihovně DLL. Že používá knihovnu DLL knihovny MFCxx.DLL, stejně jako ultimate klientské aplikace. To umožňuje opakovaně použitelné listu tříd, opakovaně použitelné základní třídy a opakovaně použitelné dokumentů a zobrazení tříd.

## <a name="pros-and-cons"></a>Výhody a nevýhody

Proč byste měli použít sdílenou verzi knihovny MFC

- Použití sdílené knihovny může způsobit menší aplikace (minimální aplikace, která používá většina knihovny MFC je menší než 10 tis.).

- Sdílených verzí knihovny MFC podporuje rozšiřující knihovny DLL MFC a běžných knihovnách MFC DLL.

- Vytváření aplikace, která používá sdílené knihovny MFC je rychlejší než sestavování aplikace staticky propojené knihovny MFC, protože není nutné samostatně propojit knihovnu MFC. To platí zejména v **ladění** sestavení, kde musí propojovací program kompaktně ladit informace – díky propojení s knihovnou DLL, která už obsahuje informace o ladění, je méně ladících informací ke spojení v rámci vaší aplikace.

Proč byste neměli používat sdílenou verzi knihovny MFC:

- Přesouvání aplikaci používající sdílené knihovny vyžaduje dodání MFCxx.DLL (a ostatní) knihovny s vaším programem. Knihovny MFCxx.DLL je volně redistribuovány, stejně jako mnoho knihoven DLL, ale stále je nutné nainstalovat knihovny DLL ve vašem instalačním programu. Kromě toho je nutné dodat MSVCRTxx.DLL, která obsahuje knihovny C runtime, který se používá i tak, že váš program a samotnými knihovnami MFC DLL.

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Jak napsat rozšiřující knihovny DLL MFC

Rozšiřující knihovna DLL MFC je knihovna DLL obsahující třídy a funkce zapisují na tomto funkce pro třídy knihovny MFC. Rozšiřující knihovna DLL MFC používá sdílené knihovny DLL MFC stejným způsobem jako aplikace, používá s několika další aspekty:

- Proces sestavení se podobá vytváření aplikace, která používá sdílené knihovny MFC s pár dalších kompilátoru a možnosti linkeru.

- Knihovna MFC DLL rozšíření nemá `CWinApp`-odvozené třídy.

- Rozšiřující knihovna DLL MFC, musíte zadat speciální `DllMain`. AppWizard poskytuje `DllMain` funkce, která můžete upravit.

- Rozšiřující knihovna DLL MFC obvykle poskytne inicializační rutina pro vytvoření `CDynLinkLibrary` MFC – rozšiřující knihovny DLL chce export-li `CRuntimeClass`no nebo prostředky do aplikace. Odvozená třída `CDynLinkLibrary` mohou být použity, pokud na aplikační data musí být udržuje MFC – rozšiřující knihovny DLL.

Tyto aspekty jsou popsány podrobněji níže. Také byste měli použít k ukázce MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md) protože ilustruje:

- Vytvoření aplikace pomocí sdílené knihovny. (DLLHUSK. Soubor EXE je aplikace knihovny MFC, která dynamicky propojuje ke knihovnám MFC také další knihovny DLL).

- Sestavování rozšiřující knihovny DLL MFC. (Všimněte si, jako speciální příznaky `_AFXEXT` , která se používají při sestavování rozšiřující knihovny DLL MFC)

- Dva příklady rozšiřující knihovny DLL MFC. Ukazuje základní struktura knihovny MFC DLL rozšíření s omezenou exporty (TESTDLL1) a další pořady export celá třída rozhraní (TESTDLL2).

Klientská aplikace a všechny rozšiřující knihovny DLL MFC musí používat stejnou verzi knihovny MFCxx.DLL. Měli byste postupovat podle konvence knihovny MFC DLL a poskytnout i ladění a maloobchodního prodeje (/ release) verzi vaší MFC – rozšiřující knihovny DLL. To umožňuje klientských programů pro sestavení ladění a prodejní verzí své aplikace a propojte je s odpovídající ladicí nebo prodejní verze produktu všechny knihovny DLL.

> [!NOTE]
>  Protože C++ pojmenujte pozměnění a exportovat problémy, exportovat seznam z rozšiřující knihovny DLL MFC může lišit mezi ladění a maloobchodní verze stejné knihovny DLL a knihovny DLL pro různé platformy. Maloobchodní MFCxx.DLL má asi 2000 exportovat vstupní bod; ladění MFCxxD.DLL má přibližně 3000 exportovat vstupní body.

### <a name="quick-note-on-memory-management"></a>Rychlé poznámky týkající se správy paměti

V části s názvem "Správu paměti a" na konci této Technická poznámka popisuje provádění MFCxx.DLL sdílených verzí knihovny MFC. Informace, které potřebujete vědět o implementaci právě rozšiřující knihovny MFC DLL je zde popsáno.

Knihovny MFCxx.DLL a všechny rozšiřující knihovny DLL MFC načtena do klientské aplikace adresní prostor bude používat stejné přidělení paměti, načítání prostředků a dalších státech MFC "globální" jako kdyby byly ve stejné aplikaci. To je důležité, protože knihovny MFC DLL a běžných knihovnách MFC DLL, která staticky se propojit s knihovnou MFC přesným opakem a každou knihovnu DLL přidělování mimo svůj vlastní fond paměti k dispozici.

Pokud rozšiřující knihovny DLL MFC přidělí paměť, pak tuto paměť můžete libovolně kombinovat s jakýkoli jiný objekt přidělený aplikace. Navíc pokud dojde k chybě aplikace používající sdílené knihovny MFC, ochranu operačního systému bude udržovat tak integritu jiné aplikace knihovny MFC, knihovny DLL pro sdílení obsahu.

Podobně jako jiné "globální" stavy knihovny MFC, jako je aktuální spustitelný soubor a načíst prostředky z, jsou také sdílené mezi klientskou aplikaci a všechny rozšiřující knihovny DLL MFC i MFCxx.DLL samotný.

### <a name="building-an-mfc-extension-dll"></a>Sestavování rozšiřující knihovny DLL MFC

AppWizard můžete použít k vytvoření projektu knihovny MFC DLL rozšíření, a automaticky vygeneruje se odpovídající kompilátor a propojovací program nastavení. Bylo také generovat `DllMain` funkce, která můžete upravit.

Pokud převádíte na rozšiřující knihovny DLL MFC existující projekt, začněte pomocí standardních pravidel pro vytvoření aplikace pomocí sdílených verzí knihovny MFC, a pak postupujte takto:

- Přidat **/D_AFXEXT** příznaky kompilátoru. V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Vyberte kategorii preprocesoru. Přidat `_AFXEXT` makra definovat pole, každou z položek, oddělení středníky.

- Odeberte **/Gy** přepínač kompilátoru. V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Potom vyberte kategorii, generování kódu. Ujistěte se, že není povolená možnost "Povolit propojování na úrovní funkcí". To usnadní Postup exportu tříd, protože linkeru nedojde k odebrání neodkazovaných funkce. Pokud původní projekt sloužící k sestavení standardní knihovny MFC DLL staticky propojené do MFC, změna **/MT [d]** – možnost kompilátoru do **/MD [d]**.

- Sestavení knihovny exportu s **/dll** možnost odkaz. Tím se nastaví, když vytvoříte nový cíl zadáte Win32 dynamickou knihovnu jako cílový typ.

### <a name="changing-your-header-files"></a>Změna hlavičkové soubory

Cílem rozšiřující knihovny DLL MFC je obvykle exportovat některé běžné funkce do jedné nebo více aplikací, které můžete použít tuto funkci. To boils k exportu tříd a globální funkce, které jsou k dispozici pro klientské aplikace.

Pokud to chcete udělat musí zajistit, že každý z členské funkce je označen jako import a export podle potřeby. To vyžaduje speciální deklarace: `__declspec(dllexport)` a `__declspec(dllimport)`. Při vaší třídy jsou používána klientskými aplikacemi, můžete je deklarovat jako `__declspec(dllimport)`. Pokud při sestavování rozšíření MFC DLL, by měly být deklarovány jako `__declspec(dllexport)`. Kromě toho funkce musí být ve skutečnosti exportován, tak, aby klientské programy vytvořit vazbu k nim v okamžiku načtení.

Chcete-li exportovat celé třídy, použijte `AFX_EXT_CLASS` v definici třídy. Toto makro je definována v rámci rozhraní jako `__declspec(dllexport)` při `_AFXDLL` a `_AFXEXT` je definován, ale definované jako `__declspec(dllimport)` při `_AFXEXT` není definován. `_AFXEXT` jak je popsáno výše, je definována pouze při sestavování vaší MFC – rozšiřující knihovny DLL. Příklad:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Export není celé třídy

Někdy můžete exportovat pouze jednotlivé nezbytné členy třídy. Například, pokud jste exportovali `CDialog`-odvozené třídy, je pouze potřeba vyexportovat konstruktoru a `DoModal` volání. Můžete to taky tyto členy pomocí knihovny DLL. Soubor DEF, ale můžete také použít `AFX_EXT_CLASS` stejným způsobem pro jednotlivé členy je potřeba vyexportovat.

Příklad:

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

Když toto provedete, můžete jej spustit do další problém vzhledem k tomu, že exportujete už všichni členové třídy. Problém je tak, jak tato práce maker knihovny MFC. Některé z makra pomocné rutiny knihovny MFC ve skutečnosti deklarujete nebo definujete datové členy. Proto tyto datové členy také potřebovat export z knihovny DLL.

DECLARE_DYNAMIC – makro například je definována takto při sestavování rozšiřující knihovny DLL MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Řádek, který začíná "statické `AFX_DATA`" je deklarace statických objektů uvnitř vaší třídy. K exportu této třídy správně a přístup k informacím o modulu runtime z klienta. Soubor EXE, je nutné exportovat tento statický objekt. Protože má statický objekt je deklarována s modifikátorem `AFX_DATA`, budete muset definovat `AFX_DATA` bude `__declspec(dllexport)` při vytváření knihovny DLL a definujte jej jako `__declspec(dllimport)` při vytváření vašeho klientského spustitelného souboru.

Jak je popsáno výše, `AFX_EXT_CLASS` tímto způsobem je již definován. Stačí znovu definovat `AFX_DATA` být stejný jako `AFX_EXT_CLASS` kolem vaší definice třídy.

Příklad:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

Knihovna MFC vždy používá `AFX_DATA` symbolu na datových položek definuje v rámci jeho makra, takže tento postup bude fungovat pro všechny tyto scénáře. Například pro DECLARE_MESSAGE_MAP bude fungovat.

> [!NOTE]
> Chcete-li exportovat celé třídy místo vybrané členy třídy, se automaticky vyexportují statické datové členy.

Stejný postup můžete použít automaticky export `CArchive` operátor extrakce pro třídy, které používají DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Exportujte operátor archivu tak, že "bracketing" deklarace tříd (umístěný ve. Soubor H) následujícím kódem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>Omezení _AFXEXT

Můžete použít _**AFXEXT** processoru symbolů pro vaše MFC – rozšiřující knihovny DLL, pokud nemáte více vrstev MFC – rozšiřující knihovny DLL. Pokud máte MFC – rozšiřující knihovny DLL, které volají nebo jsou odvozeny z tříd ve vlastním MFC – rozšiřující knihovny DLL, které pak jsou odvozeny z třídy knihovny MFC, musíte použít vlastní symbol preprocesoru Chcete-li předejít nejednoznačnosti.

V čem problém spočívá tohoto v systému Win32, musíte explicitně deklarovat všechna data jako `__declspec(dllexport)` pokud export z knihovny DLL a `__declspec(dllimport)` Pokud má být importována z knihovny DLL. Při definování `_AFXEXT`, hlaviček knihovny MFC, zkontrolujte, zda `AFX_EXT_CLASS` je správně definován.

Pokud máte více vrstev, jeden symbol, jako `AFX_EXT_CLASS` nestačí, protože rozšiřující knihovny DLL MFC může exportovat nové třídy, jak jako jiné třídy importovat z jiné MFC – rozšiřující knihovny DLL. Aby bylo možné řešení tohoto problému, použijte speciální symbol preprocesoru, která označuje, že vytváříte samotná knihovna DLL oproti použití knihovny DLL. Představte si například dvě rozšiřující knihovny DLL MFC, A.DLL a B.DLL. Každá exportovat některé třídy v A.H B.H. B.DLL používá třídy z A.DLL. Soubory hlaviček by vypadat přibližně takto:

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

Při vytváření A.DLL, je sestavena s **/DA_IMPL** a při vytváření B.DLL, je sestavena s **/DB_IMPL**. Když použijete samostatné symboly pro každou knihovnu DLL, exportu CExampleB a CExampleA je importován při vytváření B.DLL. CExampleA je vyexportovali při vytváření A.DLL a importován při použití B.DLL (nebo jiného klienta).

Tento typ vrstvení nelze provést, při použití předdefinované `AFX_EXT_CLASS` a `_AFXEXT` symboly preprocesoru. Tento problém není na rozdíl od způsobem mechanismus knihovna MFC sama používá při sestavování rozšiřující knihovny DLL, která jeho OLE, databáze a knihovny MFC sítě řeší techniky popsané výše.

### <a name="not-exporting-the-entire-class"></a>Export není celé třídy

Znovu budete muset provést zvláštní pozornost při neexportujete celá třída. Je nutné zajistit, že jsou správně exportovány potřebná data položky vytvořené pomocí maker knihovny MFC. To můžete udělat tak, že znovu definujete `AFX_DATA` makra vaší konkrétní třídy. To by mělo být provedeno kdykoli neexportujete celá třída.

Příklad:

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

Následuje přesný kód, který byste měli umístit do hlavní zdrojový soubor pro rozšíření MFC DLL. Poté, co obsahuje standardní by měl mít. Všimněte si, že při použití AppWizard vytvořit počáteční soubory pro rozšiřující knihovny DLL MFC, poskytne `DllMain` za vás.

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

Volání `AfxInitExtensionModule` zachytává moduly runtime – třídy (`CRuntimeClass` struktury) i jeho objekty pro vytváření objektů (`COleObjectFactory` objektů) pro použití novější při `CDynLinkLibrary` je vytvořen objekt. (Volitelné) volání `AfxTermExtensionModule` umožňuje knihovny MFC k vyčištění MFC – rozšiřující knihovny DLL při každém odpojení procesu (která se stane při ukončení procesu, nebo pokud kvůli uvolnění knihovny DLL `FreeLibrary` volání) z MFC – rozšiřující knihovny DLL. Protože většina MFC – rozšiřující knihovny DLL nejsou načtené dynamicky (obvykle jsou propojeny prostřednictvím jejich knihovny importu), volání `AfxTermExtensionModule` není obvykle nutné.

Pokud vaše aplikace načte nebo uvolní MFC – rozšiřující knihovny DLL dynamicky, je nutné volat `AfxTermExtensionModule` jak je znázorněno výše. Také je potřeba použít `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkce Win32 `LoadLibrary` a `FreeLibrary`) Pokud vaše aplikace používá více vláken, nebo pokud dynamicky načtení rozšiřující knihovny DLL MFC. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když je načteny nebo uvolněny MFC – rozšiřující knihovny DLL nejsou poškozeny globální stav knihovny MFC.

Soubor hlaviček AFXDLLX. H obsahuje speciální definice strukturám používaným v rozšiřující knihovny DLL MFC, jako je například definice `AFX_EXTENSION_MODULE` a `CDynLinkLibrary`.

Globální *extensionDLL* musí být deklarován, jak je znázorněno. Na rozdíl od 16bitové verze knihovny MFC, přidělení paměti a volání funkcí knihovny MFC během této doby od MFCxx.DLL je plně inicializován době vaše `DllMain` je volána.

### <a name="sharing-resources-and-classes"></a>Sdílení prostředků a třídy

Jednoduché rozšiřující knihovny DLL MFC potřebovat exportovat pouze několik funkcí s malou šířkou pásma klientská aplikace a nic víc. Další náročné knihovny DLL uživatelského rozhraní chtít exportovat prostředky a třídy jazyka C++ do klientské aplikace.

Export prostředků se provádí prostřednictvím seznamu prostředků. V každé žádosti je jednotlivě propojený seznam `CDynLinkLibrary` objekty. Při hledání pro určitý prostředek, podívejte se nejprve sledovat aktuální modul prostředků většinu standardní implementace MFC, který se načítá prostředky (`AfxGetResourceHandle`) a, pokud nebyla nalezena procházení seznamu `CDynLinkLibrary` objekty pokusu o načtení požadovaný prostředek.

Dynamické vytváření objektů jazyka C++ název třídy C++ se podobá. Mechanismus serializace objektu knihovny MFC musí mít všechny `CRuntimeClass` registrované objekty tak, aby mohl rekonstruovat dynamicky vytvořením objekt jazyka C++ vyžaduje typu založeného na co byla uložena dříve.

Pokud chcete, aby klientská aplikace použít třídy v rozšíření MFC DLL, které jsou `DECLARE_SERIAL`, je nutné exportovat třídy bude viditelná pro klientské aplikace. Tím se taky dělá návod `CDynLinkLibrary` seznamu.

V případě ukázce MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md), seznamu vypadá přibližně takto:

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

Knihovny MFCxx.DLL je obvykle poslední v seznamu prostředků a třídy. Knihovny MFCxx.DLL zahrnuje všechny standardní prostředky MFC, včetně řetězce výzev pro všechny identifikátory standardních příkazů. Uvedení na konec seznamu umožňuje knihovny DLL a vlastní klientské aplikace nebudete chtít své vlastní kopii standardní prostředky MFC, ale chcete-li využívají sdílené prostředky do knihovny MFCxx.DLL místo.

Sloučení prostředků tak názvy tříd všech knihoven DLL do oboru názvů klientské aplikace má nevýhodou, že budete muset pečlivě jaké ID nebo názvy, které vyberete. Můžete samozřejmě tuto funkci můžete zakázat tak, že vyexportujete buď není prostředky nebo `CDynLinkLibrary` objektu do klientské aplikace. [DLLHUSK](../overview/visual-cpp-samples.md) ukázka spravuje sdílený prostředek oboru názvů pomocí více souborů záhlaví. Zobrazit [Technická poznámka 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) další tipy pro používání souborů sdílených prostředků.

### <a name="initializing-the-dll"></a>Inicializace knihovny DLL

Jak je uvedeno výše, obvykle můžete vytvořit `CDynLinkLibrary` objektu, abyste mohli exportovat třídy a prostředky do klientské aplikace. Je potřeba poskytnout exportovaný vstupní bod inicializace knihovny DLL. Minimálně to je void rutinu, která nepřijímá žádné argumenty a vrací hodnotu nothing, ale může být cokoliv, co vám vyhovuje.

Každá klientská aplikace, která chce používat vaše knihovna DLL musí volat tato rutina inicializace, pokud použijete tento přístup. Také to může přidělit `CDynLinkLibrary` objektu ve vašich `DllMain` bezprostředně po volání `AfxInitExtensionModule`.

Musíte vytvořit inicializační rutina `CDynLinkLibrary` objekt haldy aktuální aplikace, svázanou s vaší MFC – rozšiřující knihovny DLL informace. To můžete udělat následujícími způsoby:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Název rutiny *InitXxxDLL* v tomto příkladu může být cokoli si pod. Nemusí být **extern "C"**, ale, že tomu tak je snazší Údržba exportovaného seznamu.

> [!NOTE]
> Pokud používáte MFC – rozšiřující knihovny DLL z běžné knihovny DLL MFC, musíte exportovat tento inicializační funkce. Tato funkce musí být volána z běžné knihovny MFC DLL před použitím všech tříd knihovny DLL MFC rozšíření nebo prostředky.

### <a name="exporting-entries"></a>Export položky

Jednoduchý způsob pro export tříd je použití `__declspec(dllimport)` a `__declspec(dllexport)` v každé třídě a globální funkce, kterou chcete exportovat. To je mnohem jednodušší, ale je méně efektivní než pojmenování každý vstupní bod (popsaných níže), protože budete mít méně kontrolu nad jaké funkce jsou exportovány, což nelze exportovat funkce podle pořadových čísel. TESTDLL1 a TESTDLL2 pomocí této metody můžete exportovat jejich položky.

Metodu efektivnější (a metodu používanou pro knihovny MFCxx.DLL) je exportovat každou položku ručně pojmenováním každá položka. Soubor DEF. Protože jsme exportujete selektivní exporty z naší knihovny DLL (tedy nikoli vše), jsme musíte se rozhodnout určité rozhraní, která nám chcete exportovat. To je obtížné, protože je nutné zadat názvy byly pozměněny linkeru ve formuláři položky v. Soubor DEF. Není exportovat všechny třídy jazyka C++, pokud je skutečně potřeba pro ni mají symbolický odkaz.

Pokud jste vyzkoušeli export C++ třídy s. DEF soubor dříve, možná budete chtít Vyviňte nástroj k automatickému vygenerování tohoto seznamu. To lze provést pomocí odkazu dvoufázový proces. Propojit vaše knihovna DLL jednou pro žádné exporty a povolit linkeru, aby generoval. Soubor s Mapováním. Na. Soubor s Mapováním je možné vytvořit seznam funkcí, které mají být exportovány, takže se některé změny uspořádání, můžete použít ke generování EXPORTU zadané pro vaše. Soubor DEF. Exportovat seznam knihovny MFCxx.DLL a technologií OLE a databáze rozšiřující knihovny DLL MFC, několik tisíc v čísle, se vygeneroval s odpovídající proces (i když není úplně automatický a vyžaduje některé ruční ladění každý jednou za chvíli).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Knihovny MFC DLL rozšíření nemá `CWinApp`-odvozenému objektu vlastní; místo toho musíte pracovat `CWinApp`-odvozenému objektu klientské aplikace. To znamená, že klientská aplikace vlastní pumpa zpráv nečinné smyčky a tak dále.

Pokud vaše knihovna DLL rozšíření MFC potřebuje udržovat doplňující data pro každou aplikaci, lze odvodit novou třídu z `CDynLinkLibrary` a vytvořte jej v InitXxxDLL rutina popisu výše. Při spuštění, knihovny DLL můžete zkontrolovat aktuální aplikace seznam `CDynLinkLibrary` objekty, abyste našli ten konkrétní rozšiřující knihovny MFC DLL.

### <a name="using-resources-in-your-dll-implementation"></a>Použití prostředků ve vaší implementaci knihovny DLL

Jak je uvedeno výše, provede zatížení prostředků výchozí seznam `CDynLinkLibrary` objekty hledáte prvního souboru EXE nebo DLL, která má požadovaný prostředek. Všechna rozhraní API knihovny MFC stejně jako všechny vnitřní kód používá `AfxFindResourceHandle` projde seznam prostředků se najít prostředek, bez ohledu na to, kde může nacházet.

Pokud chcete načíst prostředky jenom na konkrétním místě, používají rozhraní API `AfxGetResourceHandle` a `AfxSetResourceHandle` uložit původní popisovač a nastavit nový popisovač. Je potřeba obnovit původní popisovač prostředku, pak se vraťte do klientské aplikace. Ukázka TESTDLL2 používá tento přístup pro explicitní načtení nabídky.

Procházení seznamu má nevýhody, že je o něco pomalejší a vyžaduje správu rozsahů ID prostředků. To má výhodu, že klientská aplikace, která obsahuje odkazy na několik rozšiřující knihovny DLL MFC můžete použít libovolný zadaná knihovna DLL prostředků bez nutnosti zadávat popisovač instance knihovny DLL. `AfxFindResourceHandle` rozhraní API slouží k procházení seznamu prostředků pro hledání shody daného. Přijímá název a typ prostředku a vrátí popisovač prostředku, ve kterém byl nalezen první (nebo hodnota NULL).

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Psaní aplikací, který používá verzi knihovny DLL

### <a name="application-requirements"></a>Požadavky na aplikace

Aplikace, která používá sdílenou verzi knihovny MFC musí postupovat podle několika jednoduchých pravidel:

- Musí mít `CWinApp` objekt a standardní pravidla pro zprávy odeslané.

- Musí být kompilovány se sadou vyžaduje kompilátor příznaky (viz níže).

- Třeba propojit s knihovnami importu MFCxx. Díky nastavení příznaků vyžaduje kompilátor, zjistit hlaviček knihovny MFC v době spojení knihovny, které aplikace by měla propojit s.

- Pokud chcete spustit spustitelný soubor, musí být MFCxx.DLL na cestě nebo v adresáři systému Windows.

### <a name="building-with-the-development-environment"></a>Sestavování s využitím vývojové prostředí

Pokud používáte interní souborů pravidel s většinou standardních výchozích hodnot, můžete snadno změnit projekt tak, aby sestavení verze knihovny DLL.

Následující krok předpokládá, že máte správně fungující aplikaci knihovny MFC s NAFXCWD spojené. LIB (pro ladění) a NAFXCW. LIB (pro maloobchodní prodej) a chcete převeďte ho na použití sdílených verzí knihovny MFC. Běží prostředí Visual C++ a mít interní projekt soubor.

1. Na **projekty** nabídky, klikněte na tlačítko **vlastnosti**. V **Obecné** stránky **výchozí nastavení projektu**, nastavte Microsoft Foundation Classes na **použít knihovnu MFC ve sdílené knihovně DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Sestavování s využitím NMAKE

Pokud používáte externí soubor pravidel funkce jazyka Visual C++, nebo používáte NMAKE přímo, budete muset upravit váš soubor pravidel pro podporu kompilátoru a možnosti linkeru

Požadované příznaky kompilátoru:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Tento symbol, který má být definována musí standardní záhlaví knihovny MFC:

- **/ MD** aplikace musí používat knihovnu DLL verze knihovny run-time jazyka C

Nastavení další příznaky kompilátoru řídí výchozími hodnotami knihovny MFC (například _DEBUG pro ladění).

Upravte seznam linkeru knihoven. Změna NAFXCWD. LIB MFCxxD.LIB a změňte NAFXCW. Nástroj LIB MFCxx.LIB. Nahraďte LIBC. LIB s MSVCRT. LIB. Stejně jako u jakékoli jiné knihovny MFC je důležité, že je umístěn MFCxxD.LIB **před** žádné knihovny C runtime.

Volitelně přidejte **/D_AFXDLL** maloobchodních a ladicích možnosti kompilátoru prostředku (ten, který skutečně sestavuje prostředky s **/R**). Díky tomu svého konečného spustitelného souboru menší prostřednictvím sdílení prostředků, které se nacházejí v knihovnách MFC DLL.

Vyžaduje se znovu sestavit, po provedení těchto změn.

### <a name="building-the-samples"></a>Ukázky vytváření

Většina ukázkové programy MFC může být sestaven z jazyka Visual C++, nebo ze sdíleného souboru pravidel NMAKE kompatibilní z příkazového řádku.

Některé z těchto ukázek použití knihovny MFCxx.DLL převést, můžete načíst. Klíč k vícenásobné aktivaci souboru do Visual C++ a nastavit možnosti projektu, jak je popsáno výše. Pokud používáte NMAKE sestavení, můžete zadat "AFXDLL = 1" na NMAKE příkazového řádku a že bude vytvoření vzorku pomocí sdílené knihovny MFC.

Ukázce MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md) využívá rozhraní DLL verze knihovny MFC. Tato ukázka nejen ukazuje, jak sestavit aplikaci propojit s MFCxx.DLL, ale také ukazuje další funkce knihovny DLL MFC možnost balení například rozšiřující knihovny DLL MFC je popsáno dále v tomto Technická poznámka.

### <a name="packaging-notes"></a>Poznámky k vytváření balíčků

Komerčně nabízenou verzi knihovny DLL (MFCxx [U]. Knihovny DLL) jsou volně redistribuovány. Ladicí verze knihoven DLL nejsou volně redistribuovány a by měla sloužit pouze během vývoje aplikace.

Ladění knihoven DLL jsou k dispozici s ladicími informacemi. Pomocí ladicího programu Visual C++, můžou sledovat provádění vaší aplikace, stejně jako knihovna DLL. Uvolnění knihovny DLL (MFCxx [U]. Knihovny DLL) neobsahují informace o ladění.

-Li přizpůsobit nebo opětovné sestavení knihovny DLL, pak byste měli volat je něco jiného než "MFCxx" The MFC SRC souboru MFCDLL. Klíč k vícenásobné aktivaci popisuje možnosti sestavení a obsahuje logiku pro přejmenování knihovny DLL. Přejmenování souborů je nezbytné, protože tyto knihovny DLL jsou potenciálně sdílet řada aplikací knihovny MFC. S vlastní verze knihovny MFC DLL nahradit nainstalované v systému způsobit nefunkčnost jiné aplikace knihovny MFC pomocí sdílené knihovny MFC DLL.

Opětovné sestavení knihovny DLL MFC se nedoporučuje.

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Jak je implementovaná MFCxx.DLL

Následující část popisuje, jak je implementované knihovny MFC DLL (MFCxx.DLL a MFCxxD.DLL). Vysvětlení, že zde nejsou podrobnosti také důležité, pokud všechny ji chcete je použít knihovnu MFC DLL s vaší aplikací. Podrobnosti zde nejsou nezbytně nutné pochopit, jak psát rozšiřující knihovny DLL MFC, ale Princip implementovaný vám mohou pomoci psát vlastní knihovny DLL.

### <a name="implementation-overview"></a>Přehled implementace

MFC DLL je ve skutečnosti zvláštním případem rozšiřující knihovna DLL MFC, jak je popsáno výše. Má velmi velký počet exportů pro velký počet tříd. Existuje několik dalších věcí uděláme v knihovně MFC DLL, které usnadňují speciální ještě více než regulární MFC – rozšiřující knihovny DLL.

### <a name="win32-does-most-of-the-work"></a>Win32 provede většinu práce

16bitové verze knihovny MFC potřeba několik speciální technik, včetně dat pro aplikaci v segmentu zásobníku speciální segmenty vytvořené nějaký kód sestavení 80 x 86, výjimek na úrovni jednotlivého procesu kontextů a další techniky. Win32 přímo podporuje za zpracování dat v knihovně DLL, která je, co chtějí ve většině případů. Ve většině případů MFCxx.DLL je právě NAFXCW. Lib – zabalené v knihovně DLL. Když se podíváte na zdrojový kód knihovny MFC, najdete velmi málo _AFXDLL #ifdef, protože existují velmi málo zvláštní případy, které je potřeba provést. Zvláštní případy, které se konkrétně existují řešit Win32 na Windows 3.1 (jinak známé jako Win32s). Win32s nemá podpora na úrovni jednotlivého procesu DLL data přímo, takže knihovny MFC DLL musí používat úložiště thread local (TLS) rozhraní API systému Win32 k získání dat místní proces.

### <a name="impact-on-library-sources-additional-files"></a>Dopad na zdroje knihovny, další soubory

Dopad **_AFXDLL** verze na normální zdroje třídy knihovny MFC a hlavičky je relativně malé. Existuje soubor speciální verzi (AFXV_DLL. H) stejně jako další záhlaví souboru (AFXDLL_. H) součástí hlavní AFXWIN. Hlavička H. AFXDLL_. Obsahuje hlavičky H `CDynLinkLibrary` třídy a další podrobnosti implementace obou `_AFXDLL` aplikací a rozšiřující knihovny DLL MFC. AFXDLLX. H záhlaví se poskytuje pro sestavování rozšiřující knihovny DLL MFC (podrobnosti naleznete v části výše).

Pravidelné zdrojů do knihovny MFC v MFC SRC mají další podmíněný kód v rámci `_AFXDLL` #ifdef. Na další zdrojový soubor (DLLINIT. CPP) obsahuje další inicializační kód knihovny DLL a dalších připevnit pro sdílenou verzi knihovny MFC.

Aby bylo možné sestavit sdílených verzí knihovny MFC, jsou k dispozici další soubory. (Podrobnosti najdete níže v tom, jak vytvořit knihovnu DLL.)

- Dvě. DEF soubory se používají pro export vstupní body DLL knihovny MFC pro ladění (MFCxxD.DEF) a (MFCxx.DEF) verzi knihovny DLL.

- Aplikace. Soubor RC (MFCDLL. RC) obsahuje všechny standardní prostředky MFC a VERSIONINFO prostředku pro knihovnu DLL.

- ODPOVĚĎ. Soubor CLW (MFCDLL. CLW) je k dispozici při procházení MFC tříd pomocí ClassWizard. Poznámka: Tato funkce není konkrétní knihovny DLL verze knihovny MFC.

### <a name="memory-management"></a>Správa paměti

Aplikace pomocí knihovny MFCxx.DLL používá běžné přidělení paměti poskytované MSVCRTxx.DLL sdílenou knihovnu DLL modulu C runtime. Aplikace, libovolný rozšiřující knihovny DLL MFC a také samotnými knihovnami MFC DLL pomocí tohoto alokátoru sdílené paměti. Pomocí sdílené knihovny DLL pro přidělení paměti lze knihovny DLL MFC přidělit paměť, která je později uvolněna aplikací nebo naopak. Protože aplikace a knihovny DLL musí používat stejnou allocator, by neměla přepsat globální C++ **operátor new** nebo **operátor delete**. Stejná pravidla platí i pro zbývající rutiny přidělení běhové paměti jazyka C (například **malloc**, **realloc**, **bezplatné**a další).

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Řadové číslovky a třída __declspec(dllexport) a pojmenování knihovny DLL

Nepoužijeme `class` **__declspec(dllexport)** funkce C++ kompilátoru. Místo toho seznam exporty je součástí zdroje knihovny tříd (MFCxx.DEF a MFCxxD.DEF). Exportují se jenom tyto vybrané sady vstupní body (funkce a data). Jiné symboly, jako je například knihovny MFC privátní implementace funkcí nebo tříd, se nebudou exportovat všechny exporty provádí ordinální číslo bez názvu řetězce v tabulce rezidenční nebo jiných rezidentní název.

Pomocí `class` **__declspec(dllexport)** může být reálnou alternativu pro vytváření knihovny DLL menší, ale v případě velké knihovny DLL jako knihovny MFC, výchozí export mechanismus má efektivitu a kapacitu omezení.

Co to znamená, že všechny je, že nám můžete zabalit velké množství funkcí ve verzi knihovny MFCxx.DLL, který je pouze přibližně 800 KB bez negativního vlivu mnohem provádění nebo rychlost načítání. Knihovny MFCxx.DLL by byl 100 tisíc větší nebyla tuto techniku použít. Také díky tomu je možné přidat další vstupní body na konci. Soubor DEF povolit jednoduchou správu verzí bez omezení rychlosti a velikosti efektivitu export podle pořadových čísel. Hlavní verze revize v knihovně tříd knihovny MFC se změní název knihovny. To znamená, MFC30. Knihovna DLL je distribuovatelné knihovny DLL obsahující verzi 3.0 tříd knihovny MFC. Upgrade této knihovny DLL, Řekněme v hypotetické 3.1 knihovny MFC, knihovny DLL by se pojmenoval MFC31. Knihovna DLL místo. Znovu při úpravě zdrojový kód knihovny MFC k vytvoření vlastní verzi knihovny MFC DLL, použijte jiný název (a ideálně bez knihovny MFC"" v názvu).

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
