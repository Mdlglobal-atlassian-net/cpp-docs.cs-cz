---
title: -GS (Kontrola zabezpečení vyrovnávací paměti) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be077ecb92a3344911431a3ecbbdd7d3dc038eab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726008"
---
# <a name="gs-buffer-security-check"></a>/GS (kontrola zabezpečení vyrovnávací paměti)

Rozpozná některá přetečení vyrovnávací paměti, která přepisují návratovou adresu funkce, adresu obslužné rutiny výjimky nebo určité typy parametrů. Přetečení vyrovnávací paměti je technika používána hackery ke zneužití kódu, která nevynucuje omezení velikosti vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```
/GS[-]
```

## <a name="remarks"></a>Poznámky

**/GS** ve výchozím nastavení zapnutá. Pokud očekáváte, že vaše aplikace mít žádná bezpečnostní rizika, použijte **/GS-**. Další informace o detekci přetečení vyrovnávací paměti, naleznete v tématu [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Kontroly zabezpečení

Pro funkce, u kterých kompilátor rozpozná možnost problémů přetečení vyrovnávací paměti, přidělí místo v zásobníku před návratovou adresou. Vstupu do funkce přiděleného místa načten *soubor cookie zabezpečení* , který je vypočten jednou při načtení modulu. Při ukončení funkce a během rozbalování rámce v 64bitových operačních systémech je zavolána pomocná funkce, která zjišťuje, zda se hodnota souboru cookie nezměnila. Jiná hodnota naznačuje, že mohlo dojít k přepsání zásobníku. Je-li zjištěna jiná hodnota, proces se ukončí.

## <a name="gs-buffers"></a>Vyrovnávací paměti GS

Kontroly zabezpečení přetečení vyrovnávací paměti se provádí na *vyrovnávací paměť GS*. Vyrovnávací paměť GS může být jedna z následujících:

- Pole, které je větší než čtyři bajty, má více než dva prvky a má typ prvků, který není typem ukazatele.

- Datová struktura, jejíž velikost je více než 8 bajtů a která neobsahuje žádné ukazatele.

- Vyrovnávací paměť přidělaná pomocí [_alloca](../../c-runtime-library/reference/alloca.md) funkce.

- Libovolná třída nebo struktura obsahující vyrovnávací paměť GS.

Následující příkazy jsou příkladem deklarace vyrovnávacích pamětí GS.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

Následující příkazy však vyrovnávací paměti GS nedeklarují. První dvě deklarace obsahují prvky typu ukazatele. Třetí a čtvrtý příkaz deklarují příliš malé pole. Pátý příkaz deklaruje strukturu, jejíž velikost na platformě x86 není více než 8 bajtů.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>Inicializace souboru cookie zabezpečení

**/GS** – možnost kompilátoru vyžaduje, že soubor cookie zabezpečení inicializovat před spuštěním jakékoli funkce používající soubor cookie. Soubor cookie zabezpečení musí být inicializován při vstupu do souboru EXE nebo DLL okamžitě. Pokud se to automaticky použít výchozí VCRuntime vstupní body: mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup, nebo _DllMainCRTStartup. Používáte-li alternativní vstupní bod, soubor cookie zabezpečení musí inicializovat ručně zavoláním [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md).

## <a name="what-is-protected"></a>Chráněné položky

**/GS** – možnost kompilátoru chrání následující položky:

- Návratová adresa volání funkce.

- Adresa obslužné rutiny výjimky pro funkci.

- Ohrožené parametry funkce.

Na všech platformách **/GS** pokusí rozpoznat přetečení vyrovnávací paměti na návratovou adresu. Přetečení vyrovnávací paměti lze snadněji zneužít na platformách jako x86 a x64, které využívají konvence volání ukládající návratovou adresu volání funkce do zásobníku.

Pokud na platformě x86 funkce používá obslužnou rutinu výjimky, kompilátor pro ochranu adresy rutiny zavede soubor cookie zabezpečení. Soubor cookie je kontrolován během odvíjení rámce.

**/GS** chrání *ohrožených parametrů* , které jsou předávány do funkce. Ohroženým parametrem je ukazatel, odkaz C++, struktura jazyka C (typ C++ POD) obsahující ukazatel či vyrovnávací paměť GS.

Ohrožený parametr je přidělen před souborem cookie nebo lokálními proměnnými. Přetečení vyrovnávací paměti může tyto parametry přepsat. Kód ve funkci, která tyto parametry používá, by mohl způsobit útok dříve, než funkce vrátí hodnotu a je provedena bezpečnostní kontrola. Aby bylo nebezpečí minimalizováno, kompilátor během prologu funkce vytváří kopii ohrožených parametrů a vkládá je pod oblast úložiště pro jakoukoli vyrovnávací paměť.

Kompilátor nevytváří kopie ohrožených parametrů v následujících situacích:

- Funkce, které neobsahují vyrovnávací paměť GS.

- Optimalizace ([možnosti /O](../../build/reference/o-options-optimize-code.md)) nejsou povoleny.

- Funkce se proměnným seznamem argumentů (...).

- Funkce, které jsou označené [naked](../../cpp/naked-cpp.md).

- Funkce obsahující jako první příkaz vložený kód sestavení.

- Parametr je používán pouze způsobem, jehož zneužití je v případě přetečení vyrovnávací paměti méně pravděpodobné.

## <a name="what-is-not-protected"></a>Nechráněné položky

**/GS** – možnost kompilátoru neposkytuje ochranu proti útokům na zabezpečení všech přetečení vyrovnávací paměti. Obsahuje-li například objekt vyrovnávací paměť a tabulku vtable, přetečení vyrovnávací paměti by mohlo tabulku vtable poškodit.

I když používáte **/GS**, vždy snažte psát bezpečný kód, který nemá žádné přetečení vyrovnávací paměti.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**.

   Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V **stránky vlastností** dialogové okno, klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Upravit **kontrola zabezpečení vyrovnávací paměti** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

## <a name="example"></a>Příklad

V této ukázce dojde k přetečení vyrovnávací paměti. Z tohoto důvodu dojde za běhu aplikace k chybě.

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)