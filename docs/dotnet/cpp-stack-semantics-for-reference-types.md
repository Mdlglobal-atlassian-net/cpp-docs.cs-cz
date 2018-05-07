---
title: C++ – sémantika zásobníku pro odkazové typy | Microsoft Docs
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
ms.openlocfilehash: b3ed886d1bdeb4972122049854b5d288767aa5b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="c-stack-semantics-for-reference-types"></a>C++ – sémantika zásobníku pro odkazové typy
Před Visual C++ 2005 instance typu odkaz může vytvářet pouze pomocí `new` haldě operátor, který vytvořil objekt na paměti. Je však nyní vytvořit instanci typu odkazu pomocí stejné syntaxe, které byste použili k vytvoření instance nativního typu v zásobníku. Ano, není potřeba použít [nové, gcnew ref](../windows/ref-new-gcnew-cpp-component-extensions.md) pro vytvoření objektu odkazového typu. A pokud objekt je mimo rozsah, kompilátor volání destruktoru objektu.  
  
## <a name="remarks"></a>Poznámky  
 Při vytváření instance typu odkaz pomocí sémantika zásobníku kompilátor interně vytvořit instanci v haldě shromážděných paměti (pomocí `gcnew`).  
  
 Pokud podpis nebo návratový typ funkce zahrnuje instanci typu odkazu-hodnota, funkce budou označeny v metadatech jako, které vyžadují zvláštní zpracování (s modreq). Tato zvláštní zpracování je aktuálně k dispozici pouze klienti Visual C++; Další jazyky aktuálně nepodporují využívání funkce nebo data, která použít odkazové typy, které jsou vytvořené pomocí sémantika zásobníku.  
  
 Jedním z důvodů používat `gcnew` (dynamické přidělování) místo zásobníku sémantiku by, pokud má tento typ žádné destruktor. Navíc pomocí odkazové typy, které jsou vytvořené pomocí sémantika zásobníku v signatury funkce nebude možné, pokud chcete, aby funkce pro jiné jazyky než Visual C++.  
  
 Kompilátor nevygeneruje kopírovacího konstruktoru pro odkazového typu. Proto pokud definujete funkci, která používá typ odkazu-hodnota v podpis, je nutné zadat kopírovací konstruktor pro typ odkazu. Kopírovací konstruktor pro typ odkaz obsahuje podpis v následujícím formátu: `R(R%){}`.  
  
 Kompilátor nevygeneruje výchozí operátor přiřazení pro odkazového typu. Operátor přiřazení umožňuje vytvořit objekt, který používá sémantika zásobníku a provést jeho inicializaci na existující objekt vytvořený sémantika zásobníku. Operátor přiřazení pro typ odkaz obsahuje podpis v následujícím formátu: `void operator=( R% ){}`.  
  
 Pokud typ vašeho destruktor uvolní důležité prostředky a používáte sémantika zásobníku pro odkazové typy, není potřeba explicitně volání destruktoru (nebo volání `delete`). Další informace o destruktory v referenčních typech najdete v tématu [destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Operátor přiřazení generované kompilátorem bude postupovat podle obvyklé standardní C++ pravidla s těmito přídavky:  
  
-   Nestatické data, která bude členy, jejichž typ je popisovač pro typ odkazu Nedávná zkopírovaný (zpracovány jako člena nestatické dat, jejichž typ je ukazatel).  
  
-   Zkopíruje všechny nestatické datový člen, jejichž typ je typ hodnoty bude bez podstruktury.  
  
-   Kteréhokoli člena nestatické dat, jejíž typ se o instanci typu odkazu se vyvolat volání konstruktoru kopie odkazového typu.  
  
 Také poskytuje kompilátor `%` unární operátor převodu instance typu odkaz vytvořený sémantika zásobníku pro jeho zdrojovým typem popisovač.  
  
 Následující odkazové typy nejsou k dispozici pro použití s sémantika zásobníku:  
  
-   [delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)  
  
-   [Pole](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu ukazuje, jak deklarovat instance odkazové typy s sémantika zásobníku, jak operátor přiřazení a kopírování konstruktor funguje a jak k chybě při inicializaci sledovací odkaz s odkaz vytvořený sémantika zásobníku.  
  
### <a name="code"></a>Kód  
  
```  
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
  
```  
98  
98  
98  
13  
13  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)