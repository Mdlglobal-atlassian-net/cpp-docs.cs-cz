---
title: 'TN033: DLL verze knihovny MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370316"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: DLL verze knihovny MFC

Tato poznámka popisuje, jak můžete použít knihovny sdílených dynamických odkazů MFCxx.DLL a MFCxxD.DLL (kde x je číslo verze knihovny MFC) s aplikacemi knihovny MFC a knihovnami DLL rozšíření knihovny MFC. Další informace o běžných knihovnách DLL knihovny MFC naleznete [v tématu Použití knihovny MFC jako součást knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Tato technická poznámka se týká tří aspektů knihoven dll. Poslední dva jsou pro pokročilejší uživatele:

- [Jak sestavit knihovnu DLL rozšíření knihovny MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Jak sestavit aplikaci knihovny MFC, která používá verzi knihovny MFC knihovny MFC knihovny DLL](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Implementace knihovny MFC sdílené dynamické propojení](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Máte-li zájem o vytvoření knihovny DLL pomocí knihovny MFC, kterou lze použít s aplikacemi bez knihovny MFC (tomu se nazývá běžná knihovna DLL knihovny MFC), přečtěte si [technickou poznámku 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Přehled podpory MFCxx.DLL: Terminologie a soubory

**Pravidelné Knihovny DLL knihovny MFC**: Používáte pravidelnou knihovnu DLL knihovny MFC k vytvoření samostatné knihovny DLL pomocí některých tříd knihovny MFC. Rozhraní přes hranice aplikace/knihovny DLL jsou rozhraní "C" a klientská aplikace nemusí být aplikace knihovny MFC.

Toto je verze podpory knihovny DLL podporovaná v knihovně MFC 1.0. Je popsán v [technické poznámce 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) a vzorku MFC Advanced Concepts [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> Od visual c++ verze 4.0 je termín **USRDLL** zastaralý a byl nahrazen běžnou knihovnou DLL knihovny MFC, která staticky odkazuje na knihovnu MFC. Můžete také vytvořit pravidelnou knihovnu DLL knihovny MFC, která dynamicky odkazuje na knihovnu MFC.

Knihovna MFC 3.0 (a vyšší) podporuje běžné knihovny DLL knihovny MFC se všemi novými funkcemi, včetně tříd OLE a Database.

**AFXDLL**: To se také označuje jako sdílená verze knihoven knihovny Knihovny MFC. Toto je nová podpora knihovny DLL přidaná v knihovně MFC 2.0. Knihovna knihovny Knihovny MFC sama o sobě je v počtu knihoven DLL (popsané níže) a klientská aplikace nebo knihovna DLL dynamicky propojuje knihovny DLL, které vyžaduje. Rozhraní přes hranice aplikace/Knihovny DLL jsou rozhraní třídy C++/MFC. Klientská aplikace musí být aplikace knihovny MFC. To podporuje všechny funkce knihovny MFC 3.0 (výjimka: UNICODE není podporovánpro třídy databáze).

> [!NOTE]
> Od verze Visual C++ verze 4.0 se tento typ dll označuje jako "rozšiřující dll.".

Tato poznámka bude používat knihovnu MFCxx.DLL k odkazování na celou sadu knihovny DLL knihovny MFC, která zahrnuje:

- Ladění: MFCxxD.DLL (kombinované) a MFCSxxD.LIB (statické).

- Verze: MFCxx.DLL (kombinovaná) a MFCSxx.LIB (statické).

- Unicode Debug: MFCxxUD.DLL (kombinované) a MFCSxxD.LIB (statické).

- Unicode Release: MFCxxU.DLL (kombinovaná) a MFCSxxU.LIB (statické).

> [!NOTE]
> The MFCSxx[U][D]. Knihovny LIB se používají ve spojení s knihovnami MFC sdílené knihovny DLL. Tyto knihovny obsahují kód, který musí být staticky propojen s aplikací nebo knihovnou DLL.

Aplikace odkazuje na odpovídající knihovny importu:

- Ladění: MFCxxD.LIB

- Vydání: MFCxx.LIB

- Ladění unicode: MFCxxUD.LIB

- Unicode Verze: MFCxxU.LIB

Knihovna DLL rozšíření knihovny MFC je knihovna DLL postavená na knihovně MFCxx.DLL (nebo ostatní sdílené knihovny DLL knihovny MFC). Zde se spustí architektura komponent knihovny MFC. Pokud odvodíte užitečnou třídu z třídy Knihovny MFC nebo vytvoříte jinou sadu nástrojů podobný knihovně MFC, můžete ji umístit do knihovny DLL. Tato dll používá MFCxx.DLL, stejně jako konečná klientská aplikace. To umožňuje opakovaně použitelné třídy listů, opakovaně použitelné základní třídy a opakovaně použitelné třídy zobrazení nebo dokumentu.

## <a name="pros-and-cons"></a>Klady a zápory

Proč používat sdílenou verzi knihovny MFC

- Použití sdílené knihovny může mít za následek menší aplikace (minimální aplikace, která používá většinu knihovny knihovny MFC je menší než 10 kB).

- Sdílená verze knihovny MFC podporuje knihovny DLL rozšíření knihovny MFC a běžné knihovny DLL knihovny MFC.

- Vytváření aplikace, která používá sdílené knihovny knihovny Knihovny MFC je rychlejší než vytváření staticky propojené aplikace knihovny MFC, protože není nutné propojit samotný knihovnu MFC. To platí zejména v sestavení **chod u ladění,** kde propojovací systém musí komprimovat informace o ladění – propojením s dll, která již obsahuje informace o ladění, je méně ladicí informace k komprimaci v rámci aplikace.

Proč byste neměli používat sdílenou verzi knihovny MFC:

- Odeslání aplikace, která používá sdílenou knihovnu, vyžaduje, abyste s programem doplnili knihovnu MFCxx.DLL (a další). Knihovna MFCxx.DLL je volně redistribuovatelná jako mnoho knihoven DLL, ale stále je nutné nainstalovat knihovnu DLL do programu SETUP. Kromě toho je nutné dodat knihovnu MSVCRTxx.DLL, která obsahuje knihovnu C-runtime, která je používána programem i samotnými knihovnami DLL knihovny MFC.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Jak napsat knihovnu DLL rozšíření knihovny MFC

Knihovna DLL rozšíření knihovny MFC je knihovna DLL obsahující třídy a funkce napsané k ozdobě funkcí tříd knihovny MFC. Knihovna DLL rozšíření knihovny MFC používá sdílené knihovny DLL knihovny MFC stejným způsobem, jakým ji používá aplikace, s několika dalšími důležité informacemi:

- Proces sestavení je podobný vytváření aplikace, která používá sdílené knihovny knihovny Knihovny MFC s několika dalšími možnostmi kompilátoru a propojovacího zařízení.

- Knihovna DLL rozšíření knihovny `CWinApp`MFC nemá odvozenou třídu.

- Knihovna DLL rozšíření knihovny `DllMain`MFC musí poskytovat speciální knihovnu . AppWizard poskytuje `DllMain` funkci, kterou můžete upravit.

- Knihovna DLL rozšíření knihovny MFC obvykle `CDynLinkLibrary` poskytuje inicializační rutinu `CRuntimeClass`k vytvoření knihovny MFC extension DLL chce exportovat es nebo prostředky do aplikace. Odvozená třída `CDynLinkLibrary` může být použita, pokud data pro aplikaci musí být udržována knihovnou DLL rozšíření knihovny MFC.

Tyto úvahy jsou podrobněji popsány níže. Měli byste také odkazovat na mfc rozšířené koncepty ukázky [DLLHUSK,](../overview/visual-cpp-samples.md) protože ilustruje:

- Vytváření aplikace pomocí sdílených knihoven. (DLLHUSK. EXE je aplikace knihovny MFC, která dynamicky odkazuje na knihovny knihovny Knihovny MFC a další knihovny DLL.)

- Vytváření knihovny DLL rozšíření knihovny MFC. (Všimněte si speciálních `_AFXEXT` příznaků, jako jsou například, které se používají při vytváření knihovny DLL rozšíření knihovny MFC)

- Dva příklady knihovny DLL rozšíření knihovny MFC. Jeden zobrazuje základní strukturu knihovny DLL rozšíření knihovny MFC s omezenými exporty (TESTDLL1) a druhý ukazuje export rozhraní celé třídy (TESTDLL2).

Klientská aplikace i všechny knihovny DLL rozšíření knihovny MFC musí používat stejnou verzi knihovny MFCxx.DLL. Měli byste dodržovat konvence knihovny MFC DLL a poskytnout ladicí i maloobchodní (/release) verzi vaší knihovny DLL rozšíření knihovny MFC. To umožňuje klientským programům vytvářet ladicí i maloobchodní verze svých aplikací a propojit je s příslušným laděním nebo maloobchodní verzí všech knihoven DLL.

> [!NOTE]
> Vzhledem k tomu, že c++ název mangling a export problémy, seznam exportu z knihovny DLL rozšíření knihovny MFC se může lišit mezi ladicí a maloobchodní verze stejné knihovny DLL a Knihovny DLL pro různé platformy. Maloobchodní MFCxx.DLL má asi 2000 exportovaných vstupních bodů; Ladicí mfcxxD.dll má asi 3000 exportovaných vstupních bodů.

### <a name="quick-note-on-memory-management"></a>Stručná poznámka ke správě paměti

Část s názvem "Správa paměti", ke konci této technické poznámky, popisuje implementaci knihovny MFCxx.DLL se sdílenou verzí knihovny MFC. Informace, které potřebujete vědět k implementaci pouze knihovny DLL rozšíření knihovny MFC, jsou popsány zde.

Knihovna MFCxx.DLL a všechny knihovny DLL rozšíření knihovny MFC načtené do adresního prostoru klientské aplikace budou používat stejný alokátor paměti, načítání prostředků a další "globální" stavy knihovny MFC, jako by byly ve stejné aplikaci. To je významné, protože knihovny DLL bez knihovny MFC a běžné knihovny DLL knihovny MFC, které staticky odkazují na knihovnu MFC, provádějí přesný opak a mají každou knihovnu DLL, která je přiděluje z vlastního fondu paměti.

Pokud knihovna DLL rozšíření knihovny MFC přiděluje paměť, pak tato paměť může volně kombinovat s jiným objektem přiděleným aplikacím. Také pokud dojde k chybě aplikace, která používá sdílené knihovny knihovny Knihovny MFC, ochrana operačního systému bude udržovat integritu jakékoli jiné aplikace knihovny MFC sdílení knihovny DLL.

Podobně jiné "globální" stavy knihovny MFC, jako je aktuální spustitelný soubor pro načtení prostředků, jsou také sdíleny mezi klientskou aplikací a všemi knihovnami DLL rozšíření knihovny MFC a také samotnými knihovnami MFCxx.DLL.

### <a name="building-an-mfc-extension-dll"></a>Vytváření knihovny DLL rozšíření knihovny MFC

Pomocí Průvodce aplikací můžete vytvořit projekt knihovny DLL rozšíření knihovny MFC a automaticky vygeneruje příslušné nastavení kompilátoru a propojovacího zařízení. Byla také generovat `DllMain` funkci, kterou můžete upravit.

Pokud převádíte existující projekt na knihovnu DLL rozšíření knihovny MFC, začněte standardními pravidly pro vytváření aplikace pomocí sdílené verze knihovny MFC a proveďte následující kroky:

- Přidejte **/D_AFXEXT** do příznaků kompilátoru. V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Pak vyberte kategorii Preprocesor. Přidejte `_AFXEXT` do pole Definovat makra a oddělte každou položku středníky.

- Odeberte přepínač kompilátoru **/Gy.** V dialogovém okně Vlastnosti projektu vyberte uzel C/C++. Pak vyberte kategorii Generování kódu. Ujistěte se, že možnost "Povolit propojení na úrovni funkce" není povolena. To usnadní export tříd, protože propojovací program neodebere neodkazované funkce. Pokud původní projekt slouží k vytvoření běžné knihovny DLL knihovny MFC staticky propojené s knihovnou MFC, změňte možnost kompilátoru **/MT[d]** na **/MD[d]**.

- Vytvořte knihovnu exportu s parametrem **/DLL** na LINK. To bude nastaveno při vytváření nového cíle a jako cílový typ bude jako cílový typ zadána knihovna win32 dynamic-link.

### <a name="changing-your-header-files"></a>Změna souborů záhlaví

Cílem knihovny DLL rozšíření knihovny MFC je obvykle exportovat některé běžné funkce do jedné nebo více aplikací, které mohou tuto funkci používat. To se scvrkává na export tříd a globální funkce, které jsou k dispozici pro klientské aplikace.

Chcete-li to provést, musíte se ujistit, že každá členská funkce je označena jako import nebo export podle potřeby. To vyžaduje zvláštní `__declspec(dllexport)` prohlášení: a `__declspec(dllimport)`. Pokud jsou vaše třídy používány klientskými aplikacemi, chcete, aby byly deklarovány jako `__declspec(dllimport)`. Při samotné knihovně DLL rozšíření knihovny MFC `__declspec(dllexport)`by měly být deklarovány jako . Kromě toho musí být funkce skutečně exportovány, aby se s nimi klientské programy v době načítání svažovaly.

Chcete-li exportovat `AFX_EXT_CLASS` celou třídu, použijte v definici třídy. Toto makro je definováno `_AFXDLL` `_AFXEXT` rámcem jako `__declspec(dllexport)` když `__declspec(dllimport)` `_AFXEXT` a je definováno, ale definováno jako když není definováno. `_AFXEXT`jak je popsáno výše, je definována pouze při vytváření knihovny DLL rozšíření knihovny MFC. Příklad:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Neexport celé třídy

Někdy můžete chtít exportovat pouze jednotlivé potřebné členy vaší třídy. Například pokud exportujete `CDialog`odvozenou třídu, budete muset exportovat pouze `DoModal` konstruktor a volání. Tyto členy můžete exportovat pomocí dll . DEF, ale můžete také `AFX_EXT_CLASS` použít v podstatě stejným způsobem na jednotlivé členy, které potřebujete exportovat.

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

Když toto provést, může dojít k další problém, protože již exportujete všechny členy třídy. Problém je ve způsobu, jakým makra knihovny MFC fungují. Několik pomocných maker knihovny MFC skutečně deklaruje nebo definuje datové členy. Proto tyto datové členy bude také nutné exportovat z dll.

Například makro DECLARE_DYNAMIC je definováno následujícím způsobem při vytváření knihovny DLL rozšíření knihovny MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Řádek, který začíná `AFX_DATA`"statické " deklaruje statický objekt uvnitř třídy. Chcete-li správně exportovat tuto třídu a získat přístup k informacím za běhu z klienta . EXE, musíte exportovat tento statický objekt. Vzhledem k tomu, že `AFX_DATA`statický objekt je `AFX_DATA` deklarován s modifikátorem , stačí definovat být `__declspec(dllexport)` při vytváření knihovny DLL a definovat ji jako `__declspec(dllimport)` při vytváření spustitelného souboru klienta.

Jak je `AFX_EXT_CLASS` uvedeno výše, je již definována tímto způsobem. Stačí jen re-definovat `AFX_DATA` být stejný `AFX_EXT_CLASS` jako kolem definice třídy.

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

Knihovna MFC `AFX_DATA` vždy používá symbol na datové položky, které definuje v rámci svých maker, takže tato technika bude fungovat pro všechny tyto scénáře. Například to bude fungovat pro DECLARE_MESSAGE_MAP.

> [!NOTE]
> Pokud exportujete celou třídu, nikoli vybrané členy třídy, budou automaticky exportovány statické datové členy.

Stejnou techniku můžete použít k `CArchive` automatickému exportu operátoru extrakce pro třídy, které používají makra DECLARE_SERIAL a IMPLEMENT_SERIAL. Exportujte operátor archivu pomocí bracketingu deklarací tříd (umístěných v . H) s následujícím kódem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Omezení _AFXEXT

Symbol předprocesoru _**AFXEXT** můžete použít pro knihovny DLL rozšíření knihovny MFC, pokud nemáte více vrstev dll rozšíření knihovny MFC. Pokud máte knihovny DLL rozšíření knihovny MFC, které volají nebo odvozují z tříd ve vlastních knihovnách DLL rozšíření knihovny MFC, které pak jsou odvozeny z tříd knihovny MFC, musíte použít vlastní symbol preprocesoru, abyste předešli nejednoznačnosti.

Problém je, že v Win32, musíte `__declspec(dllexport)` explicitně deklarovat všechna data, `__declspec(dllimport)` jako kdyby má být exportován z DLL a pokud má být importován z DLL. Při definování `_AFXEXT`, záhlaví knihovny MFC ujistěte se, že `AFX_EXT_CLASS` je definovánsprávně.

Pokud máte více vrstev, jeden `AFX_EXT_CLASS` symbol, jako je například není dostačující, protože knihovna DLL rozšíření knihovny MFC může být export nových tříd, stejně jako import ovat jiné třídy z jiné ho dll rozšíření knihovny MFC. Chcete-li tento problém vyřešit, použijte speciální symbol preprocesoru, který označuje, že vytváříte samotnou knihovnu DLL versus pomocí knihovny DLL. Představte si například dvě knihovny DLL rozšíření knihovny MFC, knihovnu A.DLL a knihovnu B.DLL. Každý z nich exportuje některé třídy v A.H a B.H. B.DLL používá třídy z A.DLL. Soubory hlaviček by vypadaly nějak takto:

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

Když je vytvořena a.Dll, je sestavena s **/DA_IMPL** a když je vytvořena b.DLL, je sestavena s **/DB_IMPL**. Pomocí samostatných symbolů pro každou dll cexampleb je exportován a CExampleA je importován při vytváření B.DLL. CExampleA se exportuje při vytváření A.DLL a importuje se při použití b.dll (nebo jiným klientem).

Tento typ vrstvení nelze provést při `AFX_EXT_CLASS` použití `_AFXEXT` vestavěných a preprocesorových symbolů. Výše popsaná technika řeší tento problém způsobem, který se neliší od mechanismu, který knihovna MFC sama používá při vytváření svých knihoven DLL rozšíření OLE, Databáze a síťový knihovny MFC.

### <a name="not-exporting-the-entire-class"></a>Neexport celé třídy

Opět platí, že budete muset věnovat zvláštní pozornost, když nejste export celé třídy. Je třeba zajistit, aby byly potřebné datové položky vytvořené makry knihovny MFC exportovány správně. To lze provést opětovnou `AFX_DATA` definicí na makro vaší konkrétní třídy. To by mělo být provedeno při každém exportu celé třídy.

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

### <a name="dllmain"></a>Dllmain

Následuje přesný kód, který byste měli umístit do hlavního zdrojového souboru pro knihovnu DLL přípony knihovny MFC. Mělo by to přijít po standardu zahrnuje. Všimněte si, že při použití AppWizard k vytvoření počáteční soubory `DllMain` pro dll rozšíření knihovny MFC, dodává a pro vás.

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

Volání `AfxInitExtensionModule` zachytí moduly runtime třídy`CRuntimeClass` (struktury) stejně jako`COleObjectFactory` jeho objekt továrny `CDynLinkLibrary` (objekty) pro pozdější použití při vytvoření objektu. (Volitelné) volání `AfxTermExtensionModule` umožňuje knihovně MFC vyčistit knihovnu DLL rozšíření knihovny MFC při každém odpojit (což se stane při `FreeLibrary` ukončení procesu nebo při uvolnění knihovny DLL v důsledku volání) z knihovny DLL rozšíření knihovny MFC. Vzhledem k tomu, že většina knihovny DLL rozšíření knihovny MFC nejsou `AfxTermExtensionModule` dynamicky načteny (obvykle jsou propojeny prostřednictvím svých knihoven importu), volání obvykle není nutné.

Pokud aplikace načte a uvolní rozšíření Knihovny DLL knihovny MFC dynamicky, nezapomeňte volat, `AfxTermExtensionModule` jak je znázorněno výše. Také nezapomeňte použít `AfxLoadLibrary` `AfxFreeLibrary` a (namísto Win32 funkce `LoadLibrary` a `FreeLibrary`) pokud vaše aplikace používá více vláken nebo pokud dynamicky načte rozšíření Knihovny DLL knihovny MFC. Použití `AfxLoadLibrary` `AfxFreeLibrary` a zajišťuje, že spuštění a vypnutí kódu, který se spustí při načtení a uvolnění knihovny DLL rozšíření knihovny MFC, nepoškodí globální stav knihovny MFC.

Hlavičkový soubor AFXDLLX. H obsahuje speciální definice pro struktury používané v knihovnách DLL `AFX_EXTENSION_MODULE` rozšíření `CDynLinkLibrary`knihovny MFC, jako je například definice pro a .

Globální *extensionDLL* musí být deklarována tak, jak je znázorněno. Na rozdíl od 16bitové verze knihovny MFC můžete během této doby přidělit funkce knihovny MFC paměti a `DllMain` volat, protože knihovna MFCxx.DLL je plně inicializována v době, kdy je volána vaše.

### <a name="sharing-resources-and-classes"></a>Sdílení zdrojů a tříd

Jednoduché knihovny DLL rozšíření knihovny MFC potřebují exportovat pouze několik funkcí s malou šířkou pásma do klientské aplikace a nic víc. Další knihovny DLL náročné na uživatelské rozhraní mohou chtít exportovat prostředky a třídy Jazyka C++ do klientské aplikace.

Export zdrojů se provádí prostřednictvím seznamu zdrojů. V každé aplikaci je singly propojený seznam `CDynLinkLibrary` objektů. Při hledání prostředku, většina standardních implementací knihovny MFC, které`AfxGetResourceHandle`načítají prostředky nejprve `CDynLinkLibrary` na aktuální modul prostředků ( ) a pokud není nalezen projít seznam objektů, které se pokoušejí načíst požadovaný prostředek.

Dynamické vytváření objektů jazyka C++ s názvem třídy C++ je podobné. Mechanismus deserializace objektu knihovny MFC musí mít všechny `CRuntimeClass` objekty registrované tak, aby jej bylo možné rekonstruovat dynamickým vytvořením objektu Jazyka C++ požadovaného typu na základě toho, co bylo uloženo dříve.

Pokud chcete, aby klientská aplikace používala třídy `DECLARE_SERIAL`v knihovně DLL rozšíření knihovny MFC , které jsou , budete muset exportovat třídy, které budou viditelné pro klientskou aplikaci. To se také provádí `CDynLinkLibrary` procházkou po seznamu.

V případě mfc advanced concepts ukázky [DLLHUSK](../overview/visual-cpp-samples.md), seznam vypadá něco jako:

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

MFCxx.DLL je obvykle poslední v seznamu zdrojů a tříd. Knihovna MFCxx.DLL obsahuje všechny standardní prostředky knihovny MFC, včetně řetězců výzev pro všechna id standardního příkazu. Umístění na konci seznamu umožňuje knihovny DLL a klientské aplikace sám nemají vlastní kopii standardní prostředky knihovny MFC, ale spoléhat na sdílené prostředky v Knihovně MFCxx.DLL místo.

Sloučení prostředků a názvů tříd všech knihoven DLL do oboru názvů klientské aplikace má nevýhodu, že musíte být opatrní, jaké ID nebo názvy vyberete. Tuto funkci můžete samozřejmě zakázat tím, že `CDynLinkLibrary` do klientské aplikace neexportujete prostředky ani objekt. Ukázka [DLLHUSK](../overview/visual-cpp-samples.md) spravuje obor názvů sdílených prostředků pomocí více souborů hlaviček. Další tipy k používání sdílených souborů prostředků najdete v [technické poznámce 35.](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

### <a name="initializing-the-dll"></a>Inicializace dll

Jak bylo uvedeno výše, obvykle budete `CDynLinkLibrary` chtít vytvořit objekt, aby bylo možné exportovat prostředky a třídy do klientské aplikace. Pro inicializaci dll. Minimálně se jedná o neplatnou rutinu, která nepřijímá žádné argumenty a nic nevrací, ale může to být cokoli, co se vám líbí.

Každá klientská aplikace, která chce používat dll musí volat tuto inicializační rutinu, pokud použijete tento přístup. Tento `CDynLinkLibrary` objekt můžete také `DllMain` přidělit `AfxInitExtensionModule`ve vašem právě po volání .

Inicializační rutina `CDynLinkLibrary` musí vytvořit objekt v haldě aktuální aplikace, připojený až k informacím knihovny DLL rozšíření knihovny MFC. To lze provést pomocí následujících akcí:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Název rutiny *InitXxxDLL* v tomto příkladu může být cokoli, co chcete. Nemusí být **extern "C"**, ale tím je export ní seznam snadněji udržovat.

> [!NOTE]
> Pokud používáte knihovnu DLL rozšíření knihovny MFC z běžné knihovny DLL knihovny MFC, je nutné tuto funkci inicializace exportovat. Tato funkce musí být volána z běžné knihovny DLL knihovny MFC před použitím všech tříd nebo prostředků dll rozšíření knihovny MFC.

### <a name="exporting-entries"></a>Export položek

Jednoduchý způsob exportu tříd je `__declspec(dllimport)` `__declspec(dllexport)` použití a pro každou třídu a globální funkci, kterou chcete exportovat. To je mnohem jednodušší, ale je méně efektivní než pojmenování každého vstupního bodu (popsané níže), protože máte menší kontrolu nad tím, jaké funkce jsou exportovány a nelze exportovat funkce řadové. TESTDLL1 a TESTDLL2 použít tuto metodu k exportu svých položek.

Účinnější metodou (a metodou používanou mfcxx.DLL) je exportovat každou položku ručně pojmenováním každé položky v . DEF. Vzhledem k tomu, že exportujeme selektivní vývozy z naší knihovny DLL (tj. ne všechno), musíme se rozhodnout, která konkrétní rozhraní chceme exportovat. To je obtížné, protože je nutné zadat pošacené názvy propojovacího nebo spojovacího pole ve formě položek v . DEF. Neexportujte žádné třídy Jazyka C++, pokud pro ni opravdu nepotřebujete mít symbolický odkaz.

Pokud jste se pokusili exportovat třídy jazyka C++ pomocí . DEF dříve, můžete vytvořit nástroj pro generování tohoto seznamu automaticky. To lze provést pomocí dvoustupňového procesu propojení. Propojte dll jednou bez exportu a povolte propojovacímu zařízení generovat . MAP. Tá. Mapový soubor lze použít ke generování seznamu funkcí, které by měly být exportovány, takže s některými přeskupení, může být použit ke generování export položky pro vaše . DEF. Export seznam pro MFCxx.DLL a OLE a rozšíření knihovny MFC rozšíření Knihovny DLL, několik tisíc v počtu, byl generován s takovým procesem (i když to není zcela automatické a vyžaduje některé ruční ladění jednou za čas).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Knihovna DLL rozšíření knihovny `CWinApp`MFC nemá vlastní objekt odvozený. místo toho musí `CWinApp`pracovat s -derived objekt klientské aplikace. To znamená, že klientská aplikace vlastní hlavní zprávy čerpadlo, nečinnosti smyčky a tak dále.

Pokud vaše knihovna MFC Extension DLL potřebuje udržovat další data `CDynLinkLibrary` pro každou aplikaci, můžete odvodit novou třídu z a vytvořit ji v rutině InitXxxDLL popsat výše. Při spuštění knihovny DLL můžete zkontrolovat aktuální `CDynLinkLibrary` aplikace seznam objektů najít jeden pro konkrétní rozšíření knihovny DLL knihovny MFC.

### <a name="using-resources-in-your-dll-implementation"></a>Použití prostředků v implementaci dll

Jak bylo uvedeno výše, výchozí zatížení prostředků `CDynLinkLibrary` bude procházet seznam objektů, které hledají první EXE nebo DLL, který má požadovaný prostředek. Všechna pravidla API knihovny MFC, `AfxFindResourceHandle` stejně jako všechny vnitřní kód používá k procházce seznamu prostředků najít všechny prostředky, bez ohledu na to, kde se může nacházet.

Pokud chcete načíst prostředky pouze z určitého `AfxGetResourceHandle` místa, použijte api a `AfxSetResourceHandle` uložit starý popisovač a nastavte nový popisovač. Nezapomeňte obnovit starý popisovač prostředků před návratem do klientské aplikace. Ukázka TESTDLL2 používá tento přístup pro explicitní načtení nabídky.

Chůze v seznamu má nevýhody, že je o něco pomalejší a vyžaduje správu rozsahů ID prostředků. Má tu výhodu, že klientská aplikace, která odkazuje na několik knihovny DLL rozšíření knihovny MFC můžete použít libovolný prostředek s dll poskytuje bez nutnosti zadat popisovač instance Knihovny DLL. `AfxFindResourceHandle`je rozhraní API používané pro chůzi seznamu prostředků hledat danou shodu. Přebírá název a typ prostředku a vrátí popisovač prostředku, kde byl poprvé nalezen (nebo NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Psaní aplikace, která používá verzi dll

### <a name="application-requirements"></a>Požadavky na aplikaci

Aplikace, která používá sdílenou verzi knihovny MFC, musí dodržovat několik jednoduchých pravidel:

- Musí mít `CWinApp` objekt a dodržovat standardní pravidla pro čerpadlo zpráv.

- Musí být kompilován se sadou požadovaných příznaků kompilátoru (viz níže).

- Musí být propojena s knihovnami importu MFCxx. Nastavením požadovaných příznaků kompilátoru určují záhlaví knihovny MFC v době propojení, se kterou knihovnou by měla aplikace propojit.

- Chcete-li spustit spustitelný soubor, mfcxx.Dll musí být na cestě nebo v systémovém adresáři systému Windows.

### <a name="building-with-the-development-environment"></a>Budování s rozvojovým prostředím

Pokud používáte interní makefile s většinou standardních výchozích hodnot, můžete snadno změnit projekt a vytvořit verzi dll.

Následující krok předpokládá, že máte správně fungující aplikaci knihovny MFC propojenou s NAFXCWD. LIB (pro ladění) a NAFXCW. LIB (pro maloobchod) a chcete jej převést tak, aby používala sdílenou verzi knihovny knihovny knihovny MFC. Spouštějíte prostředí Visual C++ a máte interní soubor projektu.

1. V nabídce **Projekty** klepněte na **položku Vlastnosti**. Na stránce **Obecné** v části **Výchozí nastavení projektu**nastavte třídy Microsoft Foundation tak, aby **používaly knihovnu MFC ve sdílené knihovně DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Budova s NMAKE

Pokud používáte externí funkci makefile visual c++ nebo používáte nmake přímo, budete muset upravit makefile pro podporu kompilátoru a propojovacího programu možnosti

Požadované příznaky kompilátoru:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Standardní hlavičky knihovny MFC musí být definovántento symbol:

- **/MD** Aplikace musí používat verzi knihovny DLL knihovny run-time c

Všechny ostatní příznaky kompilátoru postupujte podle výchozích hodnot knihovny MFC (například _DEBUG pro ladění).

Upravte seznam knihoven propojovacího systému. Změnit NAFXCWD. LIB na MFCxxD.LIB a změnit NAFXCW. LIB na MFCxx.LIB. Vyměňte LIBC. LIB s MSVCRT. Lib. Stejně jako u jiných knihovny Knihovny MFC je důležité, aby MFCxxD.LIB je umístěn **před** všechny knihovny C-runtime.

Volitelně přidat **/D_AFXDLL** do možností kompilátoru maloobchodních i ladicích prostředků (ten, který ve skutečnosti zkompiluje prostředky s **/R**). Díky konečné spustitelný soubor menší sdílení prostředků, které jsou k dispozici v knihovnách DLL knihovny MFC.

Po provedení těchto změn je vyžadováno úplné opětovné sestavení.

### <a name="building-the-samples"></a>Vytváření vzorků

Většina ukázkových programů knihovny MFC může být vytvořena z jazyka Visual C++ nebo ze sdíleného makefile kompatibilního s NMAKE z příkazového řádku.

Chcete-li převést některý z těchto vzorků použít MFCxx.DLL, můžete načíst . MAK do visual c++ a nastavte možnosti projektu, jak je popsáno výše. Pokud používáte sestavení NMAKE, můžete zadat "AFXDLL=1" na příkazovém řádku NMAKE a který vytvoří ukázku pomocí sdílených knihoven knihovny MFC.

Ukázka knihovny MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md) je vytvořena s verzí knihovny MFC knihovny MFC knihovny MFC. Tato ukázka nejen ukazuje, jak vytvořit aplikaci propojenou s knihovnou MFCxx.DLL, ale také ilustruje další funkce možnosti balení Knihovny MFC DLL, jako jsou knihovny DLL rozšíření knihovny MFC popsané dále v této technické poznámce.

### <a name="packaging-notes"></a>Poznámky k balení

Maloobchodní verze knihoven DLL (MFCxx[U]. DLL) jsou volně redistribuovatelné. Ladicí verze knihovny DLL nejsou volně redistribuovatelné a měly by být použity pouze při vývoji aplikace.

Ladicí knihovny DLL jsou k dispozici s informacemi o ladění. Pomocí ladicího programu Visual C++ můžete sledovat spuštění aplikace i dll. DLL release (MFCxx[U]. DLL) neobsahují informace o ladění.

Pokud upravíte nebo znovu vytvoříte knihovny DLL, měli byste je nazvat něčím jiným než knihovnou MFCxx Soubor SRC knihovny MFC MFCDLL. Mak popisuje možnosti sestavení a obsahuje logiku pro přejmenování dll. Je nezbytné přejmenovat soubory, protože tyto knihovny DLL jsou potenciálně sdíleny mnoha aplikacemi knihovny MFC. Pokud vlastní verze knihoven DLL knihovny MFC nahradíte ty, které jsou nainstalovány v systému, může dojít k přerušení jiné aplikace knihovny MFC pomocí sdílených knihoven DLL knihovny MFC.

Opětovné sestavení knihovny DLL knihovny MFC se nedoporučuje.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Jak je implementována mfcxx.dll

Následující část popisuje, jak je implementována knihovna MFC DLL (MFCxx.DLL a MFCxxD.DLL). Pochopení podrobnosti zde také nejsou důležité, pokud vše, co chcete udělat, je použít knihovnu DLL knihovny MFC s vaší aplikací. Podrobnosti zde nejsou nezbytné pro pochopení, jak napsat knihovnu DLL rozšíření knihovny MFC, ale pochopení této implementace vám může pomoci napsat vlastní knihovnu DLL.

### <a name="implementation-overview"></a>Přehled implementace

Knihovna DLL knihovny MFC je skutečně zvláštní případ knihovny DLL rozšíření knihovny MFC, jak je popsáno výše. Má velmi velký počet vývozů pro velký počet tříd. Existuje několik dalších věcí, které děláme v knihovně DLL knihovny MFC, díky kterým je ještě více zvláštní než běžné rozšíření knihovny DLL knihovny MFC.

### <a name="win32-does-most-of-the-work"></a>Win32 dělá většinu práce

16bitová verze knihovny MFC potřebovala řadu speciálních technik, včetně dat pro aplikaci v segmentu zásobníku, speciálních segmentů vytvořených některým kódem sestavení 80x86, kontexty výjimek pro každý proces a dalších technik. Win32 přímo podporuje data na zpracování v dll, což je to, co chcete většinu času. Z větší části MFCxx.DLL je jen NAFXCW. LIB zabalená v dll. Pokud se podíváte na zdrojový kód knihovny MFC, najdete jen velmi málo #ifdef _AFXDLL, protože existuje jen velmi málo zvláštních případů, které je třeba provést. Zvláštní případy, které jsou tam jsou konkrétně řešit Win32 v systému Windows 3.1 (jinak známý jako Win32s). Win32s nepodporuje data knihovny DLL pro každý proces přímo, takže knihovna MFC DLL musí k získání místních dat procesu použít rozhraní API pro místní úložiště (TLS).

### <a name="impact-on-library-sources-additional-files"></a>Dopad na zdroje knihovny, další soubory

Dopad **_AFXDLL** verze na normální zdroje knihovny tříd knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny je poměrně menší. K dispozici je speciální verze souboru (AFXV_DLL. H) a další soubor záhlaví (AFXDLL_. H) zahrnuto v hlavním AFXWIN. H záhlaví. Ten AFXDLL_. H záhlaví `CDynLinkLibrary` obsahuje třídu a `_AFXDLL` další podrobnosti implementace obou aplikací a knihovny DLL rozšíření knihovny MFC. The AFXDLLX. H záhlaví je k dispozici pro vytváření knihovny DLL rozšíření knihovny MFC (podrobnosti viz výše).

Pravidelné zdroje knihovny Knihovny MFC v knihovně MFC `_AFXDLL` SRC mají některé další podmíněný kód pod #ifdef. Další zdrojový soubor (DLLINIT. CPP) obsahuje další kód inicializace knihovny DLL a další připevnění pro sdílenou verzi knihovny MFC.

Za účelem vytvoření sdílené verze knihovny MFC jsou k dispozici další soubory. (Podrobnosti o vytvoření dll.)

- Dva. Soubory DEF se používají pro export vstupních bodů Knihovny MFC DLL pro ladění (MFCxxD.DEF) a vydání (MFCxx.DEF) verze dll.

- A . RC soubor (MFCDLL. RC) obsahuje všechny standardní prostředky knihovny MFC a prostředek VERSIONINFO pro knihovnu DLL.

- A. SOUBOR CLW (Knihovna MFCDLL. CLW) je k dispozici pro prohlížení tříd knihovny MFC pomocí ClassWizard. Poznámka: Tato funkce není zvláštní verze knihovny MFC Knihovny DLL.

### <a name="memory-management"></a>Správa paměti

Aplikace používající mfcxx.dll používá společný alokátor paměti poskytovaný msvcrtxx.DLL, sdílenou dll c-runtime. Aplikace, všechny knihovny DLL rozšíření knihovny MFC a také knihovny DLL knihovny MFC používají tento alokátor sdílené paměti. Pomocí sdílené knihovny DLL pro přidělení paměti knihovny MFC knihovny DLL můžete přidělit paměť, která je později uvolněna aplikací nebo naopak. Vzhledem k tomu, že aplikace i dll musí používat stejný alokátor, neměli byste přepsat globální operátor C++ **nový** nebo **operátor odstranit**. Stejná pravidla platí pro zbytek rutiny přidělení paměti za běhu jazyka C (například **malloc**, **realloc**, **free**a další).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Řadové názvy a __declspec třídy (dllexport) a pojmenování dll.

Nepoužíváme `class` **funkci __declspec(dllexport)** kompilátoru Jazyka C++. Místo toho seznam exportů je součástí zdrojů knihovny tříd (MFCxx.DEF a MFCxxD.DEF). Exportují se pouze tyto vybrané sady vstupních bodů (funkcí a dat). Jiné symboly, například funkce nebo třídy soukromé implementace knihovny MFC, nejsou exportovány Všechny exporty se provádějí podle pravidla bez názvu řetězce v tabulce rezidentních nebo nerezidentních názvů.

Použití `class` **__declspec(dllexport)** může být životaschopnou alternativou pro vytváření menších knihoven DLL, ale v případě velké knihovny DLL, jako je knihovna MFC, má výchozí mechanismus exportu omezení efektivity a kapacity.

Co to všechno znamená, že můžeme zabalit velké množství funkcí ve verzi MFCxx.DLL, která je pouze kolem 800 KB bez kompromisů hodně spuštění nebo rychlost načítání. MFCxx.DLL by byl o 100 kB větší, kdyby tato technika nebyla použita. To také umožňuje přidat další vstupní body na konci . DEF, který umožňuje jednoduchou správu verzí, aniž by byla ohrožena rychlost a účinnost velikosti exportu podle řadového čísla. Hlavní revize verzí v knihovně tříd knihovny MFC změní název knihovny. Tedy MFC30. Knihovna DLL je redistribuovatelná knihovna DLL obsahující verzi 3.0 knihovny tříd knihovny MFC. Upgrade této knihovny DLL, řekněme v hypotetické knihovně MFC 3.1, knihovna DLL by se jmenovala MFC31. Místo toho dll. Opět platí, že pokud upravíte zdrojový kód knihovny MFC k vytvoření vlastní verze knihovny DLL knihovny MFC, použijte jiný název (a nejlépe jeden bez "MFC" v názvu).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
