---
title: C++ – sémantika zásobníku pro odkazové typy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: df14886daa04d4905502341ef345c3e3afa595ff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410621"
---
# <a name="c-stack-semantics-for-reference-types"></a>C++ – sémantika zásobníku pro odkazové typy

Před Visual C++ 2005, instanci typu odkazu může vytvořit pouze pomocí `new` haldě operátor, který vytvořil objekt na uvolňování paměti. Můžete však nyní vytvořit instanci typu odkazu pomocí stejné syntaxe, které můžete použít k vytvoření instance nativního typu v zásobníku. Proto není potřeba použít [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) pro vytvoření objektu typu odkazu. A když objekt dostane mimo rozsah, kompilátor vyvolá destruktor objektu.

## <a name="remarks"></a>Poznámky

Při vytváření instance typu odkazu pomocí – sémantika zásobníku kompilátoru interně vytvořit instanci na haldě uvolňování paměti (pomocí `gcnew`).

Při podpisu nebo návratový typ funkce zahrnuje instanci typu odkazu podle hodnoty, funkce budou označeny v metadatech jako, které vyžadují zvláštní zpracování (s modreq). Tato zvláštní zpracování je nyní k dispozici pouze klienty jazyka Visual C++; Další jazyky momentálně nepodporují používání funkce nebo data, která použít odkazové typy vytvořené pomocí – sémantika zásobníku.

Jedním z důvodů použití `gcnew` (dynamického přidělování) namísto zásobníku sémantiku by, pokud typ nemá žádný destruktor. Také pomocí odkazové typy vytvořené pomocí – sémantika zásobníku v signaturách funkce nebude možné, pokud chcete, aby vaše funkce, které mají zpracovávat jiné jazyky než Visual C++.

Kompilátor nevygeneruje kopírovacího konstruktoru pro typ odkazu. Proto pokud definujete funkci, která se používá v podpisu typ odkazu podle hodnoty, je nutné definovat kopírovacího konstruktoru pro typ odkazu. Kopírovací konstruktor pro typ odkazu nemá podpis v následujícím formátu: `R(R%){}`.

Kompilátor nevygeneruje výchozí operátor přiřazení pro typ odkazu. Operátor přiřazení můžete vytvořit objekt pomocí – sémantika zásobníku a inicializujte ji s existující objekt vytvořený pomocí – sémantika zásobníku. Operátor přiřazení pro typ odkazu nemá podpis v následujícím formátu: `void operator=( R% ){}`.

Pokud váš typ destruktor uvolní důležitých prostředků a použít – sémantika zásobníku pro odkazové typy, není potřeba explicitně zavolat destruktor (nebo volat `delete`). Další informace o destruktorech v referenčních typech najdete v tématu [destruktory a finalizační metody v tom, jak: definice a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Operátor přiřazení vygenerované kompilátorem bude postupovat podle obvyklých pravidel C++ standard s těmito přídavky:

- Jakékoli nestatické datové členy, jehož typ je popisovač pro typ odkazu budou Nedávná zkopírovaný (zpracovalo se jako nestatický datový člen, jehož typ je ukazatel).

- Zkopíruje všechny nestatický datový člen, jehož typ je typ hodnoty budou bez podstruktury.

- Žádný nestatický datový člen, jehož typ je instanci typu odkazu se vyvolá volání kopie konstruktoru typu odkazu.

Kompilátor poskytuje také `%` unární operátor převodu instance typu odkazu, který je vytvořen pomocí – sémantika zásobníku na svůj podkladový typ popisovače.

Následující typy odkazu nejsou k dispozici pro použití s – sémantika zásobníku:

- [delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)

- [Pole](../windows/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad kódu ukazuje, jak deklarovat výskyty odkazové typy se sémantikou zásobníku, jak se operátor přiřazení a funguje konstruktor kopie a tom, jak inicializovat sledovací odkaz s odkazovým typem vytvořené pomocí – sémantika zásobníku.

### <a name="code"></a>Kód

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Výstup

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Viz také

[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)