---
title: 'TN033: DLL verze knihovny MFC | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c47f7888c2801af4dae1a181e4eb836dde4feaaa
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123003"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: DLL verze knihovny MFC

Tato poznámka se popisuje, jak můžete použít MFCxx.DLL a MFCxxD.DLL (kde x je číslo verze knihovny MFC) sdílet dynamické knihovny s aplikací MFC a MFC – rozšiřující knihovny DLL. Další informace o pravidelných MFC – knihovny DLL najdete v tématu [pomocí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Tato technická Poznámka zahrnuje tři aspekty knihoven DLL. Poslední dva jsou pro pokročilejší uživatele:

- [Tom, jak sestavit knihovny MFC DLL rozšíření](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Tom, jak sestavit aplikaci MFC, která používá DLL verze knihovny MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Jak MFC sdílené knihovny DLL jsou implementované](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Pokud vás zajímá vytváření knihovny DLL pomocí MFC, který lze použít s aplikacemi mimo MFC (to se označuje jako běžné knihovny MFC DLL), podívejte se na [Technická poznámka 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Přehled podpory MFCxx.DLL: terminologie a soubory

**Běžné knihovny MFC DLL**: používat běžné knihovny MFC DLL vytvořit samostatné knihovny DLL pomocí některé z třídy knihovny MFC. Rozhraní přes hranice aplikace/DLL jsou rozhraní "C" a klientská aplikace nemusí být aplikací knihovny MFC.

Toto je verze podpora DLL v MFC 1.0 podporovány. Je popsán v [Technická poznámka 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) a ukázkové MFC rozšířené koncepty [DLLScreenCap](../visual-cpp-samples.md).

> [!NOTE]
> Od verze Visual C++ verze 4.0 termín **USRDLL** je zastaralá a nahradila ji běžné knihovny DLL MFC, který staticky odkazuje na knihovny MFC. Může také vytvořit běžný MFC DLL, která propojuje ke knihovně MFC.

MFC 3.0 (a vyšší) podporuje regulární MFC – knihovny DLL s všechny nové funkce, včetně třídy OLE a databáze.

**AFXDLL –**: to se také označuje jako sdílené verze knihoven MFC. Toto je nová podpora DLL přidán do MFC 2.0. Klientská aplikace nebo knihovny DLL dynamicky propojuje knihovny DLL, které jsou potřeba samotné knihovny MFC je počet knihovny DLL (popsaný níže). Rozhraní přes hranice aplikace/DLL jsou C + +/ rozhraní MFC třídy. Klientská aplikace musí být aplikace knihovny MFC. To podporuje všechny funkce MFC 3.0 (výjimka: UNICODE není podporován pro databázové třídy).

> [!NOTE]
> Od verze Visual C++ verze 4.0 Tento typ knihovny DLL se označuje jako "Rozšiřující knihovny DLL."

Tato poznámka použije MFCxx.DLL k odkazování na celou nastavit MFC DLL, která zahrnuje:

- Ladění: MFCxxD.DLL (zkombinované) a MFCSxxD.LIB (statické).

- Verze: MFCxx.DLL (zkombinované) a MFCSxx.LIB (statické).

- Ladění kódu Unicode: MFCxxUD.DLL (zkombinované) a MFCSxxD.LIB (statické).

- Verze Unicode: MFCxxU.DLL (zkombinované) a MFCSxxU.LIB (statické).

> [!NOTE]
> MFCSxx [U] [D]. LIB knihovny se používají ve spojení s knihovny MFC sdílené knihovny DLL. Tyto knihovny obsahovat kód, který musí být staticky propojené do aplikace nebo DLL.

Odkazy aplikace odpovídající knihoven importovat:

- Ladění: MFCxxD.LIB

- Verze: MFCxx.LIB

- Ladění kódu Unicode: MFCxxUD.LIB

- Verze Unicode: MFCxxU.LIB

"Knihovna MFC rozšíření DLL" je založena na MFCxx.DLL knihovny DLL (nebo jiné MFC sdílené knihovny DLL). Architektura součástí MFC zde spustí. Pokud užitečné třída odvozena od třídy knihovny MFC nebo sestavení jiné MFC jako toolkit, ho můžete umístit v knihovně DLL. Knihovny DLL použije MFCxx.DLL, stejně jako ultimate klientská aplikace. To umožňuje opakovaně použitelné listu třídy, opakovaně použitelný základní třídy a třídy opakovaně použitelné zobrazení či dokumentu.

## <a name="pros-and-cons"></a>Výhody a nevýhody

Proč mám použít sdílené verze knihovny MFC

- Použití sdílené knihovny může mít za následek menší aplikace (minimální aplikace, která používá většina knihovny MFC je menší než 10 tisíc).

- Sdílené verze knihovny MFC podporuje MFC – knihovny DLL rozšíření a běžné knihovny MFC DLL.

- Vytváření aplikace, která používá sdílené knihovny MFC je rychlejší než vytvoření staticky propojené aplikace MFC, protože není potřeba propojit MFC sám sebe. To platí hlavně v **ladění** sestavení, kde musí linkeru compact informace o ladění – propojíte s knihovny DLL, která již obsahuje informace o ladění, je menší informace o ladění, chcete-li komprimovat v rámci vaší aplikace.

Proč by neměl používat sdílené verze knihovny MFC:

- Přesouvání aplikace, která používá sdílenou knihovnu vyžaduje dodáte MFCxx.DLL (a ostatních) knihovny s vaším programem. MFCxx.DLL je volně redistributable jako mnoho knihoven DLL, ale stále je nutné nainstalovat knihovny DLL v instalačním programu. Kromě toho je nutné dodat MSVCRTxx.DLL, který obsahuje knihovna C runtime, která se používá jak podle vašeho programu a knihovny MFC DLL sami.

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Jak napsat knihovnu DLL

Knihovna MFC DLL rozšíření je knihovny DLL obsahující třídy a funkce zapsána na tomto funkce třídy MFC. Knihovna MFC DLL rozšíření používá sdílené knihovny MFC DLL v stejným způsobem jako aplikace, používá několik dalších aspektů:

- Proces sestavení je podobná vytváření aplikace, která používá sdílené knihovny MFC s několik dalších kompilátoru a linkeru možnosti.

- Knihovna MFC DLL rozšíření nemá `CWinApp`-odvozené třídy.

- Knihovna MFC DLL rozšíření musíte zadat speciální `DllMain`. Poskytuje objekty AppWizard `DllMain` funkce, která můžete upravit.

- Knihovna MFC DLL rozšíření se obvykle nabízejí rutina pro inicializaci k vytvoření `CDynLinkLibrary` Pokud rozšíření MFC DLL, které chcete exportovat `CRuntimeClass`es nebo prostředky pro aplikaci. Odvozené třídy z `CDynLinkLibrary` mohou být použity, pokud pro aplikační data musí být zachovaná rozšíření MFC DLL.

Tyto aspekty jsou podrobněji popsané v níže. Musí se také podívat na ukázku rozšířené koncepty MFC [DLLHUSK](../visual-cpp-samples.md) protože ilustruje:

- Sestavení aplikace pomocí sdílené knihovny. (DLLHUSK. Aplikace MFC, který dynamicky odkazuje na knihovny MFC a také další knihovny DLL je EXE.)

- Vytváření knihovnu DLL. (Všimněte si speciální příznaky, jako například `_AFXEXT` které se používají při vytváření knihovnu DLL)

- Dva příklady MFC – knihovny DLL rozšíření. Jeden ukazuje základní struktura knihovny MFC DLL rozšíření s omezenou exportuje (TESTDLL1) a služby jiných zobrazí export celou třídu rozhraní (TESTDLL2).

Klientská aplikace i rozšíření žádné MFC – knihovny DLL musí používat stejnou verzi nástroje MFCxx.DLL. Měli byste podle konvence knihovny MFC DLL a zadejte oba ladění a maloobchodní (/ release) verzi vaší MFC – rozšiřující knihovny DLL. To umožňuje klientských programů pro ladění a prodejní verze na svými aplikacemi pro sestavení a propojit je s příslušnou ladění nebo maloobchodní verze všechny knihovny DLL.

> [!NOTE]
>  Protože C++ název pozměnění a exportovat problémy, může být seznamu export z knihoven DLL rozšíření MFC liší ladění a prodejní verze stejné knihovny DLL a knihovny DLL pro různé platformy. Prodejní MFCxx.DLL má o 2000 exportovaných vstupních bodů; ladění MFCxxD.DLL má o 3000 exportovat vstupní body.

### <a name="quick-note-on-memory-management"></a>Rychlé Poznámka na Správa paměti

V části s názvem "Správa paměti," téměř na konci této technické poznámky, popisuje provádění MFCxx.DLL sdílené verze knihovny MFC. Informace, že potřebujete vědět, abyste mohli implementovat právě rozšiřující MFC DLL je zde popsán.

MFCxx.DLL a všechna rozšíření MFC DLL načtena do adresního prostoru klientská aplikace bude používat stejné přidělení paměti, načítání prostředků a jiné "globální" stavy knihovny MFC jako kdyby byly ve stejné aplikaci. To je důležité, protože knihovny MFC DLL a regulární knihovny MFC DLL, která buď staticky přesný opak a každou knihovnu DLL přidělování mimo svůj vlastní fond paměti k dispozici.

Pokud knihovnu DLL přidělí paměť, pak tuto paměť můžete libovolně kombinovat s jakýkoliv jiný objekt přidělené aplikace. Navíc pokud dojde k chybě aplikace, která používá sdílené knihovny MFC, ochranu operačního systému bude uchovávat integritu jiné aplikace MFC sdílení knihovny DLL.

Podobně jako jiné "globální" stavy MFC, jako je aktuální spustitelný soubor načtení zdrojů, jsou také sdílené mezi klientská aplikace a všechny MFC – knihovny DLL rozšíření a také MFCxx.DLL sám sebe.

### <a name="building-an-mfc-extension-dll"></a>Vytváření rozšíření MFC DLL

Můžete použít k vytvoření projektu knihovny MFC DLL rozšíření objekty AppWizard a automaticky vygeneruje odpovídající kompilátoru a linkeru nastavení. Bylo také generovat `DllMain` funkce, která můžete upravit.

Pokud převádíte existujícího projektu na knihovnu DLL, začínat standardní pravidla pro sestavení aplikace pomocí sdílené verze knihovny MFC, a poté proveďte následující kroky:

- Přidat **/D_AFXEXT** k příznaky kompilátoru. V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Potom vyberte kategorii, preprocesoru. Přidat `_AFXEXT` na pole definovat makra oddělení jednotlivé položky oddělte středníkem.

- Odeberte **/Gy** přepínače kompilátoru. V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Potom vyberte kategorii, generování kódu. Ujistěte se, jestli není zapnutá možnost "Povolit propojení na úrovni funkcí". To bude usnadňují exportu tříd, protože linkeru nebude odebrat neodkazované funkce. Pokud původní projekt slouží k vytvoření běžný MFC DLL staticky propojené do MFC, změny **/MT [d]** – možnost kompilátoru k **/MD [d]**.

- Sestavení již exportu knihovny se **/dll** možnost propojení. To bude možné nastavit při vytváření nové cíl, zadání Win32 dynamickou knihovnu jako cílový typ.

### <a name="changing-your-header-files"></a>Změna vaše soubory hlaviček

Cílem knihovnu DLL je obvykle exportovat některé běžné funkce do jedné nebo více aplikací, které tuto funkci můžete používat. To boils na export tříd a globální funkce, které jsou k dispozici pro klientské aplikace.

Pokud to chcete provést musí zajistit, že každý z členské funkce je označena jako importovat nebo exportovat podle potřeby. To vyžaduje speciální deklarace: `__declspec(dllexport)` a `__declspec(dllimport)`. Pokud vaše třídy se používá klientskými aplikacemi, chcete, aby deklarovat jako `__declspec(dllimport)`. Když sestavujete rozšíření MFC DLL, musí být deklarována jako `__declspec(dllexport)`. Kromě toho funkce musí být ve skutečnosti exportován, tak, aby programy klienta vázání na ně době zatížení.

Chcete-li exportovat celou třídu, použijte `AFX_EXT_CLASS` v definici třídy. Toto makro je definováno rámcem jako `__declspec(dllexport)` při `_AFXDLL` a `_AFXEXT` je definován, ale definován jako `__declspec(dllimport)` při `_AFXEXT` není definován. `_AFXEXT` jak je popsáno výše, je definována pouze při vytváření vašeho MFC – rozšiřující knihovny DLL. Příklad:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Export není celý – třída

V některých případech můžete exportovat pouze jednotlivé nezbytné členy vaší třídy. Například pokud chcete exportovat `CDialog`-odvozené třídy, můžete potřebovat pouze pro export konstruktoru a `DoModal` volání. Můžete exportovat tito členové pomocí knihovny DLL. DEF souboru, ale můžete také použít `AFX_EXT_CLASS` stejným způsobem na jednotlivé členy, je třeba exportovat.

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

Když to uděláte, můžete spustit do dalšího problému vzhledem k tomu, že už exportujete všichni členové třídy. Problém je způsobem, které pracují maker MFC. Řadu makra pomocné knihovny MFC ve skutečnosti deklarovat nebo definovat datových členů. Proto tyto datové členy také potřebovat export z knihovny DLL.

DECLARE_DYNAMIC – makro například je definován následujícím způsobem při sestavování knihovnu DLL:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \

```

Na řádku, která začíná "statické `AFX_DATA`" je deklarování statického objektu uvnitř vaší třídy. Tato třída správně exportovat a přístup k informacím runtime z klienta. EXE, musíte exportovat tento statický objekt. Protože je statický objekt je deklarovaný s modifikátorem `AFX_DATA`, potřebujete definovat `AFX_DATA` být `__declspec(dllexport)` při vytváření knihovny DLL a definovat jako `__declspec(dllimport)` při sestavování vašeho klientského spustitelného souboru.

Jak je popsáno výše, `AFX_EXT_CLASS` již je definována v tímto způsobem. Potřebujete jenom znovu definovat `AFX_DATA` být stejný jako `AFX_EXT_CLASS` kolem definice vaší třídy.

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

Knihovna MFC vždy používá `AFX_DATA` symbol na datových položek, které definuje v rámci jeho makra, takže tento postup funguje u všech scénářů. Například budou fungovat v DECLARE_MESSAGE_MAP –.

> [!NOTE]
> Pokud chcete exportovat celou třídu místo vybrané členy třídy, exportují se automaticky členy statických dat.

Stejným způsobem můžete automaticky exportovat `CArchive` operátor extrakce pro třídy, které používají declare_serial – a implement_serial – makra. Export operátor archivu pomocí "bracketing" deklarace tříd (umístěný ve. Soubor H) s následujícím kódem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>Omezení _AFXEXT

Můžete použít _**AFXEXT** před procesoru symbol pro vaše MFC – rozšiřující knihovny DLL, pokud nemáte více vrstev MFC – rozšiřující knihovny DLL. Pokud máte MFC – rozšiřující knihovny DLL, které volají nebo odvozena od třídy ve vlastních MFC – rozšiřující knihovny DLL, které pak odvozena od třídy MFC, musíte použít vlastní – symbol preprocesoru aby se zabránilo nejednoznačnosti.

Problém je, že v Win32, musí explicitně deklarovat všechna data jako `__declspec(dllexport)` Pokud mají být exportovány z knihovny DLL, a `__declspec(dllimport)` má-li importovat z knihovny DLL. Když definujete `_AFXEXT`, hlavičky knihovny MFC Ujistěte se, že `AFX_EXT_CLASS` správnou definici.

Pokud máte více vrstev, jeden symbol, jako `AFX_EXT_CLASS` nestačí, protože knihovnu DLL může být exportovat nové třídy a také importovat jiné třídy z jiné MFC – rozšiřující knihovny DLL. Chcete-li řešit potíže, použijte speciální symbol preprocesoru, která určuje, že vytváříte samotné knihovny DLL a kdy knihovnu DLL. Představte si například dvě MFC rozšiřující knihovny DLL, A.DLL a B.DLL. Každá exportovat některé třídy v A.H B.H. B.DLL používá třídy z A.DLL. Soubory hlaviček by vypadat přibližně takto:

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

Když je A.DLL sestavena, je sestavena s **/DA_IMPL** a když je B.DLL sestavena, je sestavena s **/DB_IMPL**. Použitím oddělených symbolů pro každou knihovnu DLL CExampleB se exportuje a CExampleA je importován při vytváření B.DLL. CExampleA je při vytváření A.DLL exportovat a importovat při použití B.DLL (nebo jiného klienta).

Tento typ vrstvení nelze provést, pokud používáte integrované `AFX_EXT_CLASS` a `_AFXEXT` preprocesoru symboly. Technik popsaných výše řeší tento problém není na rozdíl od způsobem mechanismus MFC samotné používá při sestavování jeho OLE, databáze a sítě MFC rozšiřující knihovny DLL.

### <a name="not-exporting-the-entire-class"></a>Export není celý – třída

Znovu budete muset provést zvláštní pozornost, pokud neexportujete celou třídu. Je nutné zajistit, aby nezbytné datové položky vytvořené makry MFC jsou exportovány správně. To lze provést tak, že znovu definujete `AFX_DATA` na makro vaší konkrétní třídy. To by mělo být provedeno kdykoli neexportujete celou třídu.

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

Zde je přesný kód, který byste měli umístit do souboru hlavní zdroje pro rozšíření MFC DLL. By měl mít po standardní zahrnuje. Všimněte si, že když použijete objekty AppWizard vytvořit počáteční soubory pro knihovnu DLL, poskytne `DllMain` za vás.

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

Volání `AfxInitExtensionModule` zaznamená moduly runtime – třídy (`CRuntimeClass` struktury) i jeho objekt Factory (`COleObjectFactory` objekty) pro použití novější při `CDynLinkLibrary` je vytvořen objekt. (Volitelné) volání `AfxTermExtensionModule` umožňuje MFC čištění rozšíření MFC DLL při každém odpojení procesu (který se stane, když proces bude ukončen, nebo když je na základě těchto uvolněna z knihovny DLL `FreeLibrary` volání) z MFC rozšiřující knihovny DLL. Protože většina MFC – rozšiřující knihovny DLL dynamicky nenačtou (obvykle, jsou propojeny prostřednictvím jejich knihoven importovat), volání `AfxTermExtensionModule` není obvykle nutné.

Pokud vaše aplikace načte a uvolní MFC – rozšiřující knihovny DLL dynamicky, nezapomeňte volat `AfxTermExtensionModule` jako v příkladu nahoře. Také je nutné používat `AfxLoadLibrary` a `AfxFreeLibrary` (místo funkce Win32 `LoadLibrary` a `FreeLibrary`) Pokud vaše aplikace používá více vláken, nebo pokud dynamicky načte knihovnu DLL. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když je rozšíření MFC DLL načítání a uvolňování nejsou poškozeny globální stav MFC.

Soubor hlaviček AFXDLLX. H obsahuje speciální definice pro struktury používané v MFC rozšiřující knihovny DLL, jako je například definici `AFX_EXTENSION_MODULE` a `CDynLinkLibrary`.

Na globální *extensionDLL* musí být deklarován, jak je vidět. Na rozdíl od 16bitové verze knihovny MFC, můžete přidělit paměť a volat funkce MFC během této doby, protože čas plně inicializována MFCxx.DLL vaší `DllMain` je volána.

### <a name="sharing-resources-and-classes"></a>Sdílení prostředků a třídy

Jednoduché rozšiřující knihovny DLL MFC potřebovat exportovat pouze několik funkcí malou šířkou pásma klientská aplikace a nic Další. Další náročné knihovny DLL uživatelského rozhraní chtít exportovat prostředky a třídy C++ do klientské aplikace.

Export zdrojů se provádí pomocí seznamu prostředků. V každé žádosti je jednotlivě propojený seznam `CDynLinkLibrary` objekty. Při hledání prostředku, většina standardní MFC implementací, které načíst prostředky, nejprve vyhledává v aktuálním modulu prostředků (`AfxGetResourceHandle`) a pokud není nalezena procházení seznam `CDynLinkLibrary` objekty pokusu o načtení požadovaný prostředek.

Dynamické vytvoření objektů jazyka C++ zadán název třídy C++ je podobný. Mechanismus deserializace objektu knihovny MFC musí mít všechny `CRuntimeClass` objekty registraci tak, aby ho mohl obnovit dynamicky vytvořením C++ objekt požadovaný typ podle co byla uložena dříve.

Pokud chcete klienta aplikace pro používání tříd ve vaší MFC – rozšiřující knihovny DLL, které jsou `DECLARE_SERIAL`, pak bude potřeba export tříd pro být viditelná pro klientské aplikace. K tomu je také potřeba proti `CDynLinkLibrary` seznamu.

V případě ukázku rozšířené koncepty MFC [DLLHUSK](../visual-cpp-samples.md), seznamu vypadá podobně jako:

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

MFCxx.DLL je obvykle poslední na prostředek a seznam tříd. MFCxx.DLL zahrnuje všechny standardní prostředky MFC, včetně řetězců pro všechny identifikátory standardních příkazů. Jeho umístění na konec seznamu umožňuje knihovny DLL a aplikace klienta k nejsou své vlastní kopie standardní prostředky MFC, ale se spoléhají na sdílené prostředky v MFCxx.DLL místo.

Slučování prostředky a názvy tříd všech knihoven DLL do oboru názvů klientské aplikace má nevýhodou, že budete muset pečlivě jaké ID nebo názvy, kterou vyberete. Samozřejmě funkci můžete zakázat tento není exportem buď vaše prostředky nebo `CDynLinkLibrary` objektu do klientské aplikace. [DLLHUSK](../visual-cpp-samples.md) ukázka spravuje obor názvů sdílený prostředek pomocí více záhlaví souborů. V tématu [Technická poznámka 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) další tipy pro používání souborů sdílených prostředků.

### <a name="initializing-the-dll"></a>Inicializace knihovny DLL

Jak je uvedeno nahoře, obvykle můžete vytvořit `CDynLinkLibrary` objektu, aby bylo možné exportovat třídy a prostředky do klientské aplikace. Musíte poskytnout exportovaný vstupní bod do inicializovat knihovnu DLL. Minimálně to je void rutiny, které nepřijímá žádné argumenty a nic, ale může být, vše, co se vám líbí.

Pokud použijete tuto metodu, musí volat každou klientskou aplikaci, která chce používat vaše knihovna DLL tento proces inicializace. Může to také přidělovat `CDynLinkLibrary` objekt v vaše `DllMain` jen po volání `AfxInitExtensionModule`.

Musíte vytvořit inicializační rutina `CDynLinkLibrary` objekt v aktuální aplikaci haldy, svázanou vaší MFC – rozšiřující knihovny DLL informace. To lze provést následujícím textem:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Název rutiny *InitXxxDLL* v tomto příkladu může být jakýkoli chcete. Nemusí být **extern "C"**, ale to Ano díky seznamu export snadněji provádět údržbu.

> [!NOTE]
> Pokud používáte rozšíření MFC DLL z běžný MFC DLL, je nutné exportovat tuto funkci inicializace. Tato funkce musí být volána z regular MFC DLL před použitím žádné knihovny MFC DLL rozšíření nebo prostředky.

### <a name="exporting-entries"></a>Export záznamů

Jednoduchý způsob exportu tříd se má používat `__declspec(dllimport)` a `__declspec(dllexport)` pro každou třídu a globální funkce, které chcete exportovat. To je mnohem jednodušší, ale je méně efektivní než pojmenování každý vstupní bod (popsaný níže), protože budete mít méně kontrolu nad jaké funkce jsou exportovány a funkce nelze exportovat podle pořadí. TESTDLL1 a TESTDLL2 tuto metodu použijte k exportu jejich položky.

Efektivnější (a metodu používanou MFCxx.DLL) je ručně exportovat všechny položky pojmenováním každou položku v. DEF soubor. Vzhledem k tomu, že jsme selektivní exportuje exportovat z našich DLL (tedy ne vše), musíte se rozhodnout jsme určité rozhraní, která jsme chcete exportovat. To je obtížné, protože pozměnění jména linkeru, musíte zadat v podobě položek v. DEF soubor. Nemáte exportovat všechny třídy C++, pokud skutečně potřebujete mít symbolický odkaz.

Pokud jste se pokusili export C++ třídy s. DEF souboru před možná budete chtít vytvořte nástroj, který má automaticky generovat tohoto seznamu. To lze provést pomocí odkazu dvoustupňový proces. Propojit Knihovnu jednou s žádným exportům, a povolit linkeru pro generování. Soubor s Mapováním. Na. Souboru s Mapováním lze vygenerovat seznam funkcí, které mají být exportovány, tak se některé Změna uspořádání může sloužit ke generování zadání EXPORTU pro vaše. DEF soubor. Export seznamu pro MFCxx.DLL OLE a databáze MFC DLL rozšíření, několika tisíc v číslo, byl vytvořen se tento proces (i když není úplně automatické a vyžaduje některé ruční ladění každých jednou za chvíli).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Knihovna MFC DLL rozšíření nemá `CWinApp`-odvozený vlastní objekt; místo toho musíte pracovat se `CWinApp`-odvozené objekt klientské aplikace. To znamená, že klientská aplikace vlastní hlavní message pump, nečinné smyčky a tak dále.

Pokud vaše knihovna MFC DLL rozšíření potřebuje spravovat doplňující data pro každou aplikaci, lze odvodit novou třídu z `CDynLinkLibrary` a vytvořte jej v InitXxxDLL rutiny popisují výše. Při spuštění, knihovnu DLL zkontrolovat seznam aktuální aplikace `CDynLinkLibrary` objekty, které chcete vyhledat konkrétní MFC rozšiřující knihovny DLL.

### <a name="using-resources-in-your-dll-implementation"></a>Pomocí prostředků v implementaci knihovny DLL

Jak je uvedeno nahoře, zatížení prostředků výchozí provede seznam `CDynLinkLibrary` objekty hledá první EXE nebo DLL, která má požadovaný prostředek. Všechna rozhraní API knihovny MFC a také všechny interní kód používá `AfxFindResourceHandle` vás najít jakémukoli prostředku, bez ohledu na to, kde může nacházet v seznamu prostředků.

Pokud chcete načíst pouze prostředky z konkrétní místo, pomocí rozhraní API `AfxGetResourceHandle` a `AfxSetResourceHandle` uložte starý popisovač a nastavit nový popisovač. Ujistěte se, že obnovit starý popisovač prostředku, pak se vraťte do klientské aplikace. Ukázka TESTDLL2 používá tento přístup explicitně načítání nabídky.

Procházení seznamem má nevýhody, že je něco pomalejší a vyžaduje správu rozsahů ID prostředků. Má výhodu v podobě, klientská aplikace, která obsahuje odkazy na několik knihoven DLL rozšíření MFC můžete jakémukoli prostředku, poskytuje knihovnu DLL bez nutnosti zadávat popisovač instance knihovny DLL. `AfxFindResourceHandle` rozhraní API slouží k procházení seznamu prostředků a hledat odpovídající shody. Přebírá název a typ prostředku a vrátí popisovač prostředku, kde byl nalezen první (nebo hodnota NULL).

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Zápis aplikaci, která používá verze knihoven DLL

### <a name="application-requirements"></a>Požadavky na aplikace

Aplikace, která používá sdílená verze knihovny MFC třeba provést několik jednoduchých pravidel:

- Musí mít `CWinApp` objektu a postupujte podle standardní pravidla pro zprávy odeslané.

- Musí být zkompilovány sadu požadované kompilátoru příznaky (viz níže).

- Je nutné propojit s importovanými knihovnami MFCxx. Nastavením příznaků požadované kompilátoru určit MFC hlavičky v době spojení knihovny, které aplikace by měla propojit s.

- Pokud chcete spustit spustitelný soubor, musí být MFCxx.DLL na cestě nebo v adresáři systému Windows.

### <a name="building-with-the-development-environment"></a>Sestavování s použitím vývojového prostředí

Pokud používáte interní makefile s většinou standardních výchozích hodnot, můžete snadno změnit projekt, který má sestavení DLL verze.

Následující krok předpokládá, že máte správně funkční aplikaci MFC propojené s NAFXCWD. LIB (pro ladění) a NAFXCW. LIB (pro prodejní verze) a chcete ji používat sdílené verze knihovny MFC převést. Běží v prostředí Visual C++ a mít soubor interní projektu.

1. Na **projekty** nabídky, klikněte na tlačítko **vlastnosti**. V **Obecné** v části **výchozí projekt**, nastavte Microsoft Foundation třídy na **použití knihovny MFC ve sdílené knihovně DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Sestavování s použitím NMAKE

Pokud používáte funkci externí makefile Visual c++, nebo přímo pomocí NMAKE, budete muset upravit váš soubor pravidel pro podporu kompilátoru a možnosti linkeru

Požadované příznaky kompilátoru:

- **/ D_AFXDLL /MD**  
  **/ D_AFXDLL**

Hlavičky standardních MFC potřebovat tento symbol, který má být definován:

- **/MD** aplikace musí používat verzi knihovny DLL běhové knihovny jazyka C

Všechny ostatní příznaky kompilátoru podle MFC výchozí hodnoty (například _DEBUG – pro ladění).

Upravte linkeru seznam knihoven. Změna NAFXCWD. LIB k MFCxxD.LIB a změňte NAFXCW. LIB k MFCxx.LIB. Nahraďte LIBC. LIB s MSVCRT. LIB. Stejně jako u jiných knihovny MFC je důležité, aby je umístěn MFCxxD.LIB **před** všech knihoven C runtime.

Volitelně můžete přidat **/D_AFXDLL** na maloobchodní a ladění – možnosti kompilátoru prostředků (ten, který ve skutečnosti zkompiluje prostředky s **/R**). Díky tomu vaší poslední spustitelný soubor menší sdílením prostředky, které jsou součástí knihovny MFC DLL.

Po provedení těchto změn je vyžadován úplné opětovné sestavení.

### <a name="building-the-samples"></a>Vytváření ukázky

Ve většině aplikací ukázka MFC se dají vytvářet z Visual C++ nebo sdíleného souboru pravidel NMAKE kompatibilní z příkazového řádku.

Všechny tyto ukázky použití MFCxx.DLL převést, můžete načíst. Klíč k vícenásobné aktivaci souboru do Visual C++ a nastavit možnosti projektu, jak je popsáno výše. Pokud používáte NMAKE sestavení, můžete zadat "AFXDLL = 1" na NMAKE příkazový řádek, který bude sestavit ukázku pomocí sdílené knihovny MFC.

Ukázka MFC rozšířené koncepty [DLLHUSK](../visual-cpp-samples.md) je vytvořené s DLL verze knihovny MFC. Tato ukázka nejen znázorňuje, jak sestavit aplikaci, propojené s MFCxx.DLL, ale kromě toho ilustruje další funkce MFC DLL možnost balení například MFC DLL rozšíření popsané dál v této technické poznámky.

### <a name="packaging-notes"></a>Poznámky k balení

Prodejní verze knihoven DLL (MFCxx [U]. Knihovny DLL) jsou volně redistributable. Ladicí verze knihoven DLL nejsou volně redistributable a slouží pouze během vývoje aplikace.

Ladění knihoven DLL jsou k dispozici s ladicími informacemi. Pomocí ladicí program Visual C++, může trasování provádění vaší aplikace a také knihovnu DLL. Knihovny DLL verze (MFCxx [U]. Knihovny DLL) neobsahuje informace o ladění.

Je-li přizpůsobit nebo znovu sestavte knihovny DLL, pak byste měli zavolat je něco než "MFCxx" MFC SRC souboru MFCDLL. Klíč k vícenásobné aktivaci popisuje možnosti sestavení a obsahuje logiku pro přejmenování knihovny DLL. Přejmenování souborů je nutné, protože tyto knihovny DLL potenciálně sdílí mnoho aplikací MFC. Má svou vlastní verzi nahradit MFC – knihovny DLL nainstalované v systému rozdělit jiná aplikace MFC použití sdílené knihovny MFC DLL.

Opětovné sestavení knihovny MFC DLL se nedoporučuje.

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Jak je implementována MFCxx.DLL

Následující část popisuje, jak je implementována MFC DLL (MFCxx.DLL a MFCxxD.DLL). Podrobnosti na tomto místě jsou také není důležité, pokud se vše, co chcete udělat, je pochopení MFC DLL pomocí aplikace. Podrobnosti na tomto místě nejsou nezbytně nutné porozumět tomu, jak napsat knihovnu DLL, ale pochopení tuto implementaci vám mohou pomoci zápisu vlastní knihovny DLL.

### <a name="implementation-overview"></a>Přehled implementace

MFC DLL je ve skutečnosti ve speciálním případě knihovny MFC DLL rozšíření, jak je popsáno výše. Má velký počet exportuje pro velký počet tříd. Existuje několik dalších věcí, které jsme provést v knihovně MFC DLL, které speciální i více než regulární rozšíření MFC DLL.

### <a name="win32-does-most-of-the-work"></a>Win32 nemá většinu práce

16bitové verze knihovny MFC nutná množství speciální postupů, včetně dat pro aplikaci v zásobníku segmentu, speciální segmenty vytvořil některé kódu sestavení 80 x 86, kontexty výjimky na proces a další metody. Win32 přímo podporuje za zpracování dat v knihovně DLL, což je chcete ve většině případů. Ve většině případů MFCxx.DLL je právě NAFXCW. LIB zabalené v knihovně DLL. Pokud se podíváte na MFC zdrojový kód, najdete v ní velmi málo #ifdef _AFXDLL vzhledem k tomu, že jsou velmi málo zvláštní případy, které je potřeba provést. Zvláštní případy, které nejsou speciálně pro řešení Win32 na systému Windows 3.1 (označováno také jako Win32s). Win32s nemá podporu na proces DLL data přímo, takže MFC DLL musí používat úložiště thread-local (TLS) rozhraní API Win32 získat proces místní data.

### <a name="impact-on-library-sources-additional-files"></a>Dopad na zdrojů knihovny, další soubory

Dopad **_AFXDLL** verze na běžné zdroje knihovny tříd MFC a hlavičky je relativně malé. Existuje soubor zvláštní verze (AFXV_DLL. H) a také další záhlaví souboru (AFXDLL_. H) v hlavní AFXWIN zahrnuty. Hlavička H. AFXDLL_. Hlavička H zahrnuje `CDynLinkLibrary` třídy a další podrobnosti implementace i `_AFXDLL` aplikace a MFC – knihovny DLL rozšíření. AFXDLLX. Hlavička H se poskytuje pro vytváření knihovny DLL rozšíření MFC (viz výše podrobnosti).

Regulární zdrojů do knihovny MFC v MFC SRC mají některé další podmíněného kód pod `_AFXDLL` #ifdef. Soubor další zdroje (DLLINIT. CPP) obsahuje další kód inicializace knihovny DLL a jiné spojovací pro sdílené verze knihovny MFC.

Chcete-li vytvořit sdílená verze knihovny MFC, jsou uvedeny další soubory. (Viz níže podrobnosti o tom, jak sestavit knihovnu DLL.)

- Dva. DEF soubory se používají pro export vstupní body MFC DLL pro ladění (MFCxxD.DEF) a verzí (MFCxx.DEF) verze knihovny DLL.

- K. RC soubor (MFCDLL. RC) obsahuje všechny standardní prostředky MFC a prostředek VERSIONINFO pro knihovnu DLL.

- A. Soubor CLW (MFCDLL. Chcete-li povolit procházení MFC – třídy pomocí ClassWizard poskytuje CLW). Poznámka: Tato funkce není konkrétní k DLL verze knihovny MFC.

### <a name="memory-management"></a>Správa paměti

Aplikace pomocí MFCxx.DLL používá společné přidělení paměti od MSVCRTxx.DLL sdílenou knihovnu DLL jazyka C runtime. Aplikace, všechny rozšiřující knihovny DLL MFC a také jako knihovny MFC DLL sami pomocí toto přidělení sdílené paměti. Pomocí sdílené knihovny DLL pro přidělení paměti knihovny MFC DLL můžete přidělit paměti, která je novější vydání, aplikací nebo naopak. Vzhledem k tomu, že aplikace a knihovny DLL musí používat stejnou allocator, by neměl přepsat globální C++ **new – operátor** nebo **delete – operátor**. Stejná pravidla použít s ostatními rutiny přidělení běhové paměti jazyka C (například **malloc –**, **realloc –**, **volné**a další).

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Řadové číslovky a třída __declspec(dllexport) a názvy knihoven DLL

Nepoužijeme `class` **__declspec(dllexport)** funkce kompilátoru C++. Místo toho seznam exportuje je součástí knihovny zdroje – třída (MFCxx.DEF a MFCxxD.DEF). Exportují se pouze tyto vyberte sadu vstupní body (funkce a data). Jiné symboly, například funkce privátní implementace MFC nebo třídy, se neexportují všechny exportuje provádějí pořadí bez názvu řetězce v tabulce trvalé nebo daného názvu.

Pomocí `class` **__declspec(dllexport)** může být přijatelná alternativa pro vytváření knihovny DLL menší, ale v případě velké knihovny DLL jako MFC, výchozí export mechanismus má efektivitu a kapacity omezení.

Co to znamená, všechny je, že jsme balíček velké množství funkce ve verzi MFCxx.DLL, který je pouze bez kompromisů mnohem provádění nebo načtení rychlost přibližně 800 KB. MFCxx.DLL by byl 100 tisíc větší kdyby byl tento postup použít. To také umožňuje přidat další vstupní body na konci tohoto. DEF soubor umožňuje jednoduchou správu verzí bez kompromisů rychlost a velikost efektivitu export podle pořadí. Hlavní verze revize v knihovně tříd MFC změní název knihovny. To znamená, MFC30. Knihovna DLL je redistributable knihovny DLL obsahující verzi 3.0 třídy knihovny MFC. Upgrade této knihovny DLL, že v hypotetický 3.1 MFC MFC31 by knihovny DLL s názvem. Knihovny DLL místo. Znovu Pokud změníte MFC zdrojový kód k vytvoření vlastní verzi knihovny MFC DLL, použijte jiný název (a ideálně bez "MFC" v názvu).

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
