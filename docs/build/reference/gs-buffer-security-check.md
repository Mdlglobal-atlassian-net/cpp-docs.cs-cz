---
title: /GS (kontrola zabezpečení vyrovnávací paměti)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 92d296e8079a9ecd8d366c46bbdad8b2ee5dc313
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439564"
---
# <a name="gs-buffer-security-check"></a>/GS (kontrola zabezpečení vyrovnávací paměti)

Rozpozná některá přetečení vyrovnávací paměti, která přepisují návratovou adresu funkce, adresu obslužné rutiny výjimky nebo určité typy parametrů. Přetečení vyrovnávací paměti je technika používána hackery ke zneužití kódu, která nevynucuje omezení velikosti vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```
/GS[-]
```

## <a name="remarks"></a>Poznámky

**/GS** je ve výchozím nastavení zapnuté. Pokud očekáváte, že aplikace nebude mít žádnou expozici zabezpečení, použijte **/GS-** . Další informace o potlačení detekce přetečení vyrovnávací paměti naleznete v tématu [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Kontroly zabezpečení

Pro funkce, u kterých kompilátor rozpozná možnost problémů přetečení vyrovnávací paměti, přidělí místo v zásobníku před návratovou adresou. Při vstupu do funkce je přidělené místo načteno pomocí *souboru cookie zabezpečení* , který je vypočítán jednou při načtení modulu. Při ukončení funkce a během rozbalování rámce v 64bitových operačních systémech je zavolána pomocná funkce, která zjišťuje, zda se hodnota souboru cookie nezměnila. Jiná hodnota naznačuje, že mohlo dojít k přepsání zásobníku. Je-li zjištěna jiná hodnota, proces se ukončí.

## <a name="gs-buffers"></a>Vyrovnávací paměti GS

Pro *vyrovnávací paměť GS*se provádí kontroly zabezpečení přetečení vyrovnávací paměti. Vyrovnávací paměť GS může být jedna z následujících:

- Pole, které je větší než čtyři bajty, má více než dva prvky a má typ prvků, který není typem ukazatele.

- Datová struktura, jejíž velikost je více než 8 bajtů a která neobsahuje žádné ukazatele.

- Vyrovnávací paměť přidělená pomocí funkce [_alloca](../../c-runtime-library/reference/alloca.md) .

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

Možnost kompilátoru **/GS** vyžaduje, aby se soubor cookie zabezpečení inicializoval předtím, než se spustí kterákoli z funkcí, které používají soubor cookie. Soubor cookie zabezpečení musí být inicializován ihned při vstupu do souboru EXE nebo knihovny DLL. To se provádí automaticky, pokud použijete výchozí vstupní body VCRuntime: mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup nebo _DllMainCRTStartup. Použijete-li alternativní vstupní bod, je nutné ručně inicializovat soubor cookie zabezpečení voláním [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md).

## <a name="what-is-protected"></a>Chráněné položky

Možnost kompilátoru **/GS** chrání následující položky:

- Návratová adresa volání funkce.

- Adresa obslužné rutiny výjimky pro funkci.

- Ohrožené parametry funkce.

Na všech platformách se **/GS** pokusí detekovat přetečení vyrovnávací paměti do návratové adresy. Přetečení vyrovnávací paměti lze snadněji zneužít na platformách jako x86 a x64, které využívají konvence volání ukládající návratovou adresu volání funkce do zásobníku.

Pokud na platformě x86 funkce používá obslužnou rutinu výjimky, kompilátor pro ochranu adresy rutiny zavede soubor cookie zabezpečení. Soubor cookie je kontrolován během odvíjení rámce.

**/GS** chrání *ohrožené parametry* , které jsou předány do funkce. Ohroženým parametrem je ukazatel, odkaz C++, struktura jazyka C (typ C++ POD) obsahující ukazatel či vyrovnávací paměť GS.

Ohrožený parametr je přidělen před souborem cookie nebo lokálními proměnnými. Přetečení vyrovnávací paměti může tyto parametry přepsat. Kód ve funkci, která tyto parametry používá, by mohl způsobit útok dříve, než funkce vrátí hodnotu a je provedena bezpečnostní kontrola. Aby bylo nebezpečí minimalizováno, kompilátor během prologu funkce vytváří kopii ohrožených parametrů a vkládá je pod oblast úložiště pro jakoukoli vyrovnávací paměť.

Kompilátor nevytváří kopie ohrožených parametrů v následujících situacích:

- Funkce, které neobsahují vyrovnávací paměť GS.

- Optimalizace ([Možnosti/o](o-options-optimize-code.md)) nejsou povolené.

- Funkce se proměnným seznamem argumentů (...).

- Funkce označené jako [holé](../../cpp/naked-cpp.md).

- Funkce obsahující jako první příkaz vložený kód sestavení.

- Parametr je používán pouze způsobem, jehož zneužití je v případě přetečení vyrovnávací paměti méně pravděpodobné.

## <a name="what-is-not-protected"></a>Nechráněné položky

Možnost kompilátoru **/GS** není chráněná proti všem útokům zabezpečení přetečení vyrovnávací paměti. Obsahuje-li například objekt vyrovnávací paměť a tabulku vtable, přetečení vyrovnávací paměti by mohlo tabulku vtable poškodit.

I když používáte **/GS**, vždy se pokusíte napsat zabezpečený kód, který nemá žádné přetečení vyrovnávací paměti.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak klikněte na **vlastnosti**.

   Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V dialogovém okně **stránky vlastností** klikněte na složku **C/C++**  .

1. Klikněte na stránku vlastností **generování kódu** .

1. Upravte vlastnost **kontroly zabezpečení vyrovnávací paměti** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

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

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
