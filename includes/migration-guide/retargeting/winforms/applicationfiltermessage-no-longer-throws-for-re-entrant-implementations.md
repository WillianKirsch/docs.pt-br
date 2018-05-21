### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a><span data-ttu-id="7e7a7-101">Application.FilterMessage não é mais gerada para implementações de reentrância de IMessageFilter.PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="7e7a7-101">Application.FilterMessage no longer throws for re-entrant implementations of IMessageFilter.PreFilterMessage</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7e7a7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7e7a7-102">Details</span></span>|<span data-ttu-id="7e7a7-103">Antes do .NET Framework 4.6.1, a chamada a uma <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> com uma <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> que chamava <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> ou <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (ao chamar <xref:System.Windows.Forms.Application.DoEvents> também) causava uma <xref:System.IndexOutOfRangeException?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="7e7a7-103">Prior to the .NET Framework 4.6.1, calling <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> with an <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> which called <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> or <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (while also calling <xref:System.Windows.Forms.Application.DoEvents>) would cause an <xref:System.IndexOutOfRangeException?displayProperty=name>.</span></span><p/><span data-ttu-id="7e7a7-104">A partir dos aplicativos destinados ao .NET Framework 4.6.1, essa exceção não é mais gerada e filtros reentrantes, conforme descrito acima, podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="7e7a7-104">Beginning with applications targeting the .NET Framework 4.6.1, this exception is no longer thrown, and re-entrant filters as described above may be used.</span></span>|
|<span data-ttu-id="7e7a7-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7e7a7-105">Suggestion</span></span>|<span data-ttu-id="7e7a7-106">Lembre-se de que <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> não será mais gerado para o comportamento <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> reentrante descrito acima.</span><span class="sxs-lookup"><span data-stu-id="7e7a7-106">Be aware that <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> will no longer throw for the re-entrant <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> behavior described above.</span></span> <span data-ttu-id="7e7a7-107">Isso afeta somente os aplicativos destinados ao .NET Framework 4.6.1. Os aplicativos destinados ao .NET Framework 4.6.1 podem recusar essa alteração (ou os aplicativos de Frameworks mais antigos podem aceitar) usando a opção de compatibilidade [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation).</span><span class="sxs-lookup"><span data-stu-id="7e7a7-107">This only affects applications targeting the .NET Framework 4.6.1.Apps targeting the .NET Framework 4.6.1 can opt out of this change (or apps targeting older Frameworks may opt in) by using the [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) compatibility switch.</span></span>|
|<span data-ttu-id="7e7a7-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="7e7a7-108">Scope</span></span>|<span data-ttu-id="7e7a7-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7e7a7-109">Edge</span></span>|
|<span data-ttu-id="7e7a7-110">Versão</span><span class="sxs-lookup"><span data-stu-id="7e7a7-110">Version</span></span>|<span data-ttu-id="7e7a7-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="7e7a7-111">4.6.1</span></span>|
|<span data-ttu-id="7e7a7-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="7e7a7-112">Type</span></span>|<span data-ttu-id="7e7a7-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7e7a7-113">Retargeting</span></span>|
|<span data-ttu-id="7e7a7-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7e7a7-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
