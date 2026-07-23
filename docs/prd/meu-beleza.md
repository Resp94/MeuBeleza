# PRD: Meu Beleza — SaaS de gestão e agendamento para negócios de beleza

## Problem Statement

Proprietários-operadores de pequenos salões, barbearias, espaços de manicure e estúdios de design de sobrancelhas administram atendimento e negócio ao mesmo tempo. A agenda costuma ficar fragmentada entre papel, memória, telefone e WhatsApp, o que provoca trabalho manual, conflitos, horários ociosos, dificuldade para coordenar profissionais, cancelamentos tardios e faltas que reduzem diretamente a receita.

Os clientes dependem da disponibilidade do proprietário ou da recepção para descobrir serviços e horários, confirmar reservas, remarcar ou cancelar. Os lembretes são inconsistentes, e o estabelecimento tem pouca visibilidade sobre ocupação, recebimentos, comissões, reincidência de faltas e desempenho operacional.

As soluções existentes frequentemente são amplas, complexas ou caras para operações pequenas. O público inicial precisa de uma aplicação orientada a agenda e redução de faltas, que preserve a simplicidade para o proprietário-operador, funcione bem no celular e cresça até equipes pequenas e organizações com várias unidades.

## Solution

Meu Beleza será um SaaS brasileiro para profissionais autônomos e pequenos negócios de beleza, inicialmente com até dez profissionais por unidade. O comprador principal será o proprietário que também atende e administra a operação.

O produto reunirá agenda, funcionamento da unidade, disponibilidade dos profissionais, catálogo de serviços, página pública de agendamento, clientes, histórico, WhatsApp transacional, cancelamento e remarcação autônomos, lista de espera, avaliações privadas, pagamentos básicos, comissões e relatórios operacionais.

O cliente poderá reservar sem criar conta: escolhe serviços, seleciona um profissional ou qualquer profissional disponível, informa nome e WhatsApp, verifica o telefone e confirma a reserva. A disponibilidade será calculada a partir da interseção entre funcionamento da unidade, jornada do profissional, exceções, serviços, duração, intervalos, reservas e bloqueios temporários. A confirmação será automática quando todas as regras forem satisfeitas.

Cada unidade conectará seu próprio número à UAZAPI. O Meu Beleza enviará somente mensagens transacionais: confirmação, lembretes, alterações, cancelamentos e avaliação pós-atendimento. Campanhas, atendimento geral e chatbot não fazem parte do MVP.

O produto será multiempresa e multiunidade, com isolamento por RLS. Existirão as personas Administrador da Plataforma, proprietário, recepção/gerência, profissional e cliente final. A assinatura do SaaS será cobrada pelo AbacatePay em faixas de profissionais ativos por unidade e consolidada por organização.

O MVP será amplo e incluirá todo o escopo descrito nesta especificação. Durante o desenvolvimento, uma versão parcial será usada por três a cinco estabelecimentos parceiros; o lançamento comercial aguardará a conclusão do escopo.

## User Stories

1. As a proprietário-operador, I want cadastrar minha organização, so that eu possa administrar meu negócio no Meu Beleza.
2. As a profissional autônomo, I want cadastrar-me usando CPF, so that eu não precise possuir CNPJ para utilizar o produto.
3. As a empresa, I want cadastrar-me usando CNPJ, so that a assinatura e os dados do negócio representem a pessoa jurídica.
4. As a proprietário, I want concluir um onboarding guiado, so that eu publique minha agenda sem precisar dominar o sistema.
5. As a proprietário, I want informar dados, endereço, contatos e descrição da unidade, so that clientes reconheçam o estabelecimento.
6. As a proprietário, I want configurar o horário de funcionamento semanal da unidade, so that reservas sejam oferecidas apenas quando o estabelecimento opera.
7. As a proprietário, I want cadastrar exceções de funcionamento por data, so that feriados e horários especiais sejam respeitados.
8. As a proprietário, I want administrar várias unidades na mesma organização, so that eu controle uma operação em expansão com um único acesso.
9. As a proprietário, I want alternar entre unidades, so that eu consulte e administre cada operação sem manter contas distintas.
10. As a proprietário, I want receber uma cobrança consolidada da organização, so that eu não precise pagar cada unidade separadamente.
11. As a proprietário, I want personalizar logo, capa, cores, políticas e informações públicas, so that a página de agendamento reflita minha marca.
12. As a proprietário, I want escolher um slug público único, so that eu divulgue um endereço simples aos clientes.
13. As a visitante, I want ser redirecionado de um slug antigo por 90 dias, so that links já divulgados continuem funcionando.
14. As a proprietário, I want cadastrar profissionais sem criar login, so that toda agenda possa existir mesmo quando um colaborador não usa o painel.
15. As a proprietário, I want gerar uma senha temporária para um profissional, so that eu conceda acesso sem enviar link de convite.
16. As a novo usuário, I want ser obrigado a trocar a senha temporária no primeiro acesso, so that apenas eu conheça minha senha definitiva.
17. As a usuário, I want recuperar minha senha por código enviado ao e-mail, so that eu recupere acesso sem intervenção do suporte.
18. As a proprietário, I want invalidar sessões e gerar nova senha temporária para um membro, so that eu restaure um acesso comprometido.
19. As a proprietário, I want atribuir o perfil de recepção/gerência, so that uma pessoa administre agendas e clientes sem acessar cobrança ou configurações críticas.
20. As a proprietário, I want atribuir o perfil profissional, so that cada colaborador veja e atualize somente sua agenda e os clientes relacionados aos seus atendimentos.
21. As a profissional, I want usar a mesma conta em organizações diferentes, so that eu não mantenha múltiplos logins.
22. As a profissional, I want ter perfis e permissões separados em cada organização, so that dados de negócios diferentes não sejam compartilhados.
23. As a proprietário, I want associar um profissional a várias unidades da organização, so that ele atenda em locais diferentes.
24. As a profissional multiunidade, I want que uma reserva em uma unidade bloqueie o mesmo horário nas outras, so that eu não seja agendado duas vezes.
25. As a proprietário, I want desativar um profissional sem apagar seu histórico, so that atendimentos e comissões anteriores permaneçam íntegros.
26. As a proprietário, I want transferir ou cancelar reservas futuras antes de desativar um profissional, so that nenhum cliente fique sem atendimento silenciosamente.
27. As a proprietário, I want manter um catálogo central de serviços, so that unidades não precisem recadastrar os mesmos serviços.
28. As a proprietário, I want ativar ou desativar serviços por unidade, so that cada local ofereça seu próprio portfólio.
29. As a proprietário, I want definir nome, categoria, descrição, preço e duração padrão de um serviço, so that a disponibilidade e o valor sejam calculados corretamente.
30. As a proprietário, I want sobrescrever preço e duração por unidade, so that diferenças operacionais entre locais sejam representadas.
31. As a proprietário, I want vincular serviços aos profissionais habilitados, so that clientes vejam apenas combinações executáveis.
32. As a proprietário, I want sobrescrever preço e duração por profissional, so that experiência e produtividade individuais sejam consideradas.
33. As a proprietário, I want configurar preço fixo, preço a partir de ou preço sob avaliação, so that serviços variáveis sejam anunciados honestamente.
34. As a cliente, I want entender quando o preço é estimado, so that eu não confunda valor mínimo com valor final.
35. As a proprietário, I want exigir duração prevista mesmo para preço variável, so that a agenda sempre consiga reservar tempo.
36. As a proprietário, I want configurar tempo de preparação e limpeza antes ou depois do serviço, so that a agenda bloqueie todo o intervalo operacional necessário.
37. As a proprietário, I want manter um preço e duração históricos dentro da reserva, so that mudanças no catálogo não alterem acordos existentes.
38. As a proprietário, I want configurar a disponibilidade semanal de cada profissional, so that sua jornada possa ser menor que o funcionamento da unidade.
39. As a proprietário, I want que novos profissionais herdem o funcionamento da unidade, so that a configuração inicial seja rápida.
40. As a proprietário, I want ajustar a disponibilidade herdada por dia, so that jornadas individuais sejam respeitadas.
41. As a proprietário, I want cadastrar folgas, férias e bloqueios parciais por data, so that exceções prevaleçam sobre a semana padrão.
42. As a proprietário, I want permitir jornadas que atravessem a meia-noite, so that eventos e horários especiais sejam representáveis.
43. As a proprietário, I want configurar a grade de início dos horários, so that reservas comecem em intervalos previsíveis.
44. As a proprietário, I want configurar antecedência mínima para reservar, so that clientes não criem horários de última hora indesejados.
45. As a proprietário, I want configurar a janela máxima de reserva, so that a agenda não fique comprometida cedo demais.
46. As a cliente, I want ver horários calculados a partir da unidade, profissional e serviço, so that eu reserve apenas opções realmente disponíveis.
47. As a recepcionista, I want consultar a mesma disponibilidade usada pela página pública, so that painel e cliente não discordem.
48. As a cliente, I want escolher primeiro os serviços, so that eu encontre profissionais capazes de executá-los.
49. As a cliente, I want escolher um profissional específico, so that eu preserve minha preferência.
50. As a cliente, I want escolher qualquer profissional disponível, so that eu encontre o primeiro horário possível.
51. As a cliente, I want reservar vários serviços consecutivos com o mesmo profissional, so that eu organize uma visita completa.
52. As a cliente, I want ver duração e preço totais antes de confirmar, so that eu compreenda o compromisso.
53. As a cliente, I want agendar sem criar conta ou senha, so that o fluxo tenha pouca fricção.
54. As a cliente novo, I want verificar meu telefone por código no WhatsApp, so that a reserva não seja criada com contato falso.
55. As a cliente recorrente, I want evitar nova verificação quando meu telefone já for confiável, so that futuras reservas sejam mais rápidas.
56. As a cliente, I want que meu horário fique bloqueado por cinco minutos na etapa final, so that outra pessoa não o tome enquanto concluo.
57. As a cliente, I want confirmação automática quando as regras forem satisfeitas, so that eu não espere aprovação manual.
58. As a cliente, I want aceitar políticas versionadas de cancelamento, atraso e dados, so that as condições estejam claras antes da reserva.
59. As a cliente, I want receber confirmação imediata pelo WhatsApp, so that eu tenha prova da reserva.
60. As a cliente, I want receber lembrete 24 horas antes, so that eu não esqueça o atendimento.
61. As a cliente, I want receber lembrete duas horas antes, so that eu me prepare para chegar.
62. As a proprietário, I want configurar os horários dos lembretes, so that a comunicação corresponda à operação.
63. As a cliente, I want que mensagens não urgentes respeitem horário silencioso, so that eu não seja incomodado de madrugada.
64. As a cliente, I want receber alterações e cancelamentos imediatamente, so that eu consiga reorganizar meu dia.
65. As a cliente, I want confirmar presença por link seguro, so that eu não precise entrar em uma conta.
66. As a cliente, I want cancelar por link seguro dentro do prazo permitido, so that o horário seja liberado sem conversa manual.
67. As a cliente, I want remarcar por link seguro, so that eu escolha outro horário sem intervenção da recepção.
68. As a cliente, I want usar comandos inequívocos como CONFIRMAR, CANCELAR e REMARCAR, so that respostas simples possam iniciar a ação correta.
69. As a cliente, I want receber o link seguro quando minha resposta for ambígua, so that o sistema não altere a reserva por engano.
70. As a proprietário, I want configurar prazo mínimo para cancelamento e remarcação, so that minha política comercial seja aplicada.
71. As a cliente, I want ser orientado a falar com o negócio quando o prazo tiver passado, so that exceções sejam decididas por uma pessoa.
72. As a recepcionista, I want registrar manualmente reservas recebidas por telefone ou WhatsApp, so that toda a agenda fique centralizada.
73. As a proprietário, I want criar reservas recorrentes semanais, quinzenais ou mensais pelo painel, so that clientes frequentes tenham horários futuros.
74. As a usuário interno, I want revisar conflitos de uma série antes de criar, so that ocorrências não sejam deslocadas automaticamente.
75. As a usuário interno, I want criar somente as ocorrências livres de uma série, so that conflitos sejam resolvidos individualmente.
76. As a recepcionista, I want transferir uma reserva para outro profissional qualificado e disponível, so that uma ausência não obrigue o cancelamento.
77. As a cliente, I want aceitar uma troca de profissional ou remarcar sem penalidade, so that eu mantenha controle sobre meu atendimento.
78. As a proprietário ou gerente, I want forçar uma sobreposição com motivo e confirmação, so that exceções reais sejam possíveis e auditáveis.
79. As a profissional, I want ser impedido de criar sobreposição comum, so that conflitos não ocorram acidentalmente.
80. As a equipe, I want que reservas sigam os estados agendado, confirmado, em atendimento e concluído, so that o estágio operacional fique claro.
81. As a equipe, I want marcar uma reserva como cancelada ou falta, so that relatórios representem o resultado real.
82. As a equipe, I want ver quando a tolerância de atraso configurada foi excedida, so that eu decida atender, remarcar ou marcar falta.
83. As a proprietário, I want impedir cancelamento automático por atraso, so that uma decisão operacional não seja tomada sem contexto.
84. As a estabelecimento, I want informar motivo ao cancelar uma reserva, so that o cliente receba uma explicação e opção de remarcar.
85. As a cliente, I want entrar em lista de espera por serviço, profissional opcional e períodos, so that eu seja avisado quando surgir vaga.
86. As a cliente em espera, I want receber um link quando surgir vaga, so that eu possa concluir a reserva.
87. As a estabelecimento, I want que a vaga continue disponível até alguém concluir, so that a lista de espera não bloqueie capacidade.
88. As a recepcionista, I want agendar a próxima visita ao concluir o atendimento, so that clientes recorrentes saiam com retorno marcado.
89. As a proprietário, I want criar automaticamente uma ficha por telefone dentro da organização, so that clientes não sejam duplicados.
90. As a proprietário multiunidade, I want histórico consolidado do cliente na organização, so that eu compreenda seu relacionamento completo.
91. As a profissional, I want ver apenas clientes relacionados aos meus atendimentos e unidades, so that privacidade e menor privilégio sejam preservados.
92. As a equipe autorizada, I want registrar preferências, observações e alertas simples, so that o atendimento seja personalizado.
93. As a proprietário, I want importar clientes por CSV com pré-validação, so that eu migre uma base existente.
94. As a proprietário, I want importar agendamentos futuros em formato separado, so that eu não precise recadastrá-los um por um.
95. As a proprietário, I want exportar relatórios em CSV, so that eu analise dados fora do sistema.
96. As a cliente, I want que cada organização tenha sua própria ficha sobre mim, so that negócios diferentes não compartilhem meus dados.
97. As a proprietário, I want conectar um número de WhatsApp por unidade, so that mensagens saiam da identidade reconhecida pelo cliente.
98. As a proprietário, I want conectar ou substituir o número por QR Code ou pareamento, so that eu ative a integração dentro do Meu Beleza.
99. As a gerente, I want consultar o status do WhatsApp sem poder substituí-lo, so that eu acompanhe falhas sem obter poder crítico.
100. As a proprietário, I want ser alertado no painel e por e-mail quando o WhatsApp desconectar, so that eu restaure o serviço.
101. As a sistema, I want manter mensagens pendentes em fila durante desconexões, so that avisos úteis sejam reenviados após reconexão.
102. As a proprietário, I want ver mensagens definitivamente falhas e reenviá-las manualmente, so that problemas não desapareçam silenciosamente.
103. As a cliente, I want receber somente mensagens transacionais necessárias à reserva, so that meu número não seja usado para campanhas.
104. As a cliente, I want controlar consentimento de marketing separadamente, so that uma futura comunicação promocional nunca seja presumida.
105. As a estabelecimento, I want personalizar modelos transacionais com variáveis seguras, so that a comunicação preserve minha voz sem perder informações obrigatórias.
106. As a cliente, I want avaliar um atendimento concluído com nota e comentário opcional, so that eu forneça retorno privado.
107. As a proprietário, I want ser alertado sobre avaliações baixas, so that eu tente recuperar a experiência do cliente.
108. As a proprietário, I want definir comissão padrão por serviço, so that o cálculo seja automatizado.
109. As a proprietário, I want sobrescrever comissão por profissional, so that contratos individuais sejam representados.
110. As a proprietário-operador, I want marcar-me sem comissão, so that o sistema não gere lançamentos inúteis.
111. As a profissional, I want que comissão seja gerada apenas após atendimento concluído, so that cancelamentos e faltas não inflem valores.
112. As a proprietário, I want corrigir atendimento concluído com motivo e auditoria, so that erros possam ser ajustados sem apagar o histórico.
113. As a equipe, I want registrar preço final, sinal, saldo e forma de pagamento, so that o atendimento tenha um fechamento financeiro básico.
114. As a equipe, I want dividir o pagamento entre Pix, dinheiro, débito, crédito ou outro meio, so that o registro reflita o recebimento real.
115. As a proprietário, I want controlar quem pode aplicar desconto ou acréscimo, so that profissionais não alterem valores sem autorização.
116. As a proprietário, I want ver faturamento por competência separado de recebimentos, so that eu diferencie produção de caixa.
117. As a proprietário, I want ver sinais retidos em categoria própria, so that eles não sejam confundidos com serviços concluídos.
118. As a proprietário, I want ver agenda de hoje e próximos atendimentos, so that eu conduza a operação diária.
119. As a proprietário, I want ver faturamento previsto, recebido e sinais, so that eu acompanhe o resultado.
120. As a proprietário, I want ver ocupação, cancelamentos e faltas, so that eu identifique perda de capacidade.
121. As a proprietário, I want ver comissões a pagar, so that eu acerte a equipe.
122. As a proprietário, I want ver clientes novos e recorrentes, so that eu acompanhe retenção.
123. As a proprietário, I want filtrar relatórios por período, unidade, profissional e serviço, so that eu investigue resultados específicos.
124. As a proprietário, I want assinar o plano Solo para um profissional, so that eu pague uma faixa adequada à operação.
125. As a proprietário, I want assinar o plano Essencial para até cinco profissionais, so that minha equipe pequena tenha preço previsível.
126. As a proprietário, I want assinar o plano Equipe para até dez profissionais, so that eu cresça sem cobrança individual por login.
127. As a proprietário, I want receber duas mensalidades de desconto no anual, so that o pagamento antecipado seja recompensado.
128. As a proprietário, I want testar todos os recursos por 14 dias sem cartão, so that eu valide o produto antes de comprar.
129. As a proprietário, I want pagar assinatura recorrente por cartão no AbacatePay, so that a renovação seja automática.
130. As a proprietário, I want pagar o anual antecipado por Pix, so that eu assine sem cartão.
131. As a proprietário, I want confirmar um upgrade antes da cobrança e ativação de profissional adicional, so that meu plano não mude sem consentimento.
132. As a proprietário, I want solicitar downgrade para o próximo ciclo, so that a redução da equipe seja refletida.
133. As a assinante inadimplente, I want sete dias de tolerância e alertas, so that eu corrija uma falha de pagamento sem interrupção imediata.
134. As a assinante suspenso, I want restaurar o acesso automaticamente após pagamento, so that eu não dependa do suporte.
135. As a assinante, I want cancelar para o fim do ciclo pago, so that eu utilize o período já adquirido.
136. As a proprietário, I want exportar dados após cancelamento, so that eu não fique aprisionado ao SaaS.
137. As a Administrador da Plataforma, I want administrar organizações, unidades, planos e assinaturas, so that eu opere o Meu Beleza.
138. As a Administrador da Plataforma, I want acompanhar indicadores globais e saúde das integrações, so that eu detecte problemas sistêmicos.
139. As a Administrador da Plataforma, I want acessar dados internos apenas para suporte justificado e auditado, so that o poder administrativo seja rastreável.
140. As a Administrador da Plataforma, I want entrar em uma área isolada do mesmo aplicativo, so that eu compartilhe componentes sem expor funções administrativas.
141. As a proprietário, I want consultar uma trilha de alterações críticas, so that eu saiba quem mudou agenda, preço, pagamento, comissão ou permissão.
142. As a usuário, I want receber notificação do navegador e e-mail sobre alterações internas relevantes, so that eu acompanhe a agenda sem usar WhatsApp interno.
143. As a recepção e profissional, I want ver a agenda atualizar em tempo real, so that mudanças feitas por outra pessoa apareçam rapidamente.
144. As a profissional, I want assinar um calendário somente leitura, so that eu veja os horários no aplicativo de calendário escolhido.
145. As a usuário móvel, I want instalar a aplicação web como atalho, so that eu a acesse como um aplicativo sem loja.
146. As a usuário, I want uma interface acessível, responsiva e navegável por teclado, so that eu utilize o produto independentemente do dispositivo ou de limitações.
147. As a proprietário, I want suporte por WhatsApp e e-mail em horário comercial, so that eu tenha ajuda humana quando necessário.
148. As a visitante, I want consultar uma página pública de status, so that eu saiba quando existe indisponibilidade geral.
149. As a operador do SaaS, I want pilotar o produto com negócios reais, so that hipóteses sejam validadas antes do lançamento comercial.
150. As a operador do SaaS, I want medir adoção, autoagendamento, confiabilidade e intenção de pagamento, so that eu decida se o piloto validou o produto.

## Implementation Decisions

- O produto e a marca serão chamados Meu Beleza. A identidade do estabelecimento predomina na página pública, acompanhada por “Agendamento por Meu Beleza”. A marca do SaaS não será removível no MVP.
- O público inicial inclui profissionais autônomos e pequenos salões, barbearias, manicures e designers de sobrancelhas. O comprador principal é o proprietário que também atende e administra.
- O lançamento inicial é exclusivo para o Brasil, em português, BRL, CPF/CNPJ e telefones brasileiros. Instantes são armazenados em UTC; cada unidade usa um fuso IANA.
- A organização é o limite comercial e de compartilhamento. Uma organização possui uma ou mais unidades. Clientes e catálogo são compartilhados dentro da organização, com visibilidade limitada pelas permissões de unidade.
- Cada unidade possui endereço, contatos, funcionamento, exceções, equipe, agenda, página pública e uma conexão UAZAPI própria.
- O mesmo profissional pode atuar em várias unidades da organização. Sua ocupação bloqueia simultaneamente as outras unidades da mesma organização. Perfis em organizações distintas não compartilham agenda.
- Autenticação será fornecida pelo Supabase Auth com e-mail e senha. Profissional de domínio e conta de login são entidades separadas.
- O proprietário cria acessos sem link de convite. A senha temporária é aleatória, mostrada uma única vez, expira em 24 horas e exige troca no primeiro acesso.
- Recuperação de senha utiliza código por e-mail. O proprietário também pode revogar sessões e gerar nova senha temporária.
- Não haverá autenticação em dois fatores no MVP. Acesso administrativo terá senha forte, limitação de tentativas, bloqueio progressivo, sessão curta e alerta de novo login.
- Perfis de autorização: Administrador da Plataforma, proprietário, recepção/gerência e profissional. Cliente final não possui conta.
- O proprietário tem acesso total à organização; recepção/gerência administra agendas e clientes sem cobrança ou configurações críticas; profissional acessa sua agenda e os clientes de seus atendimentos; Administrador da Plataforma opera o SaaS.
- Todo acesso de suporte administrativo exige justificativa e auditoria. Nenhum usuário comum pode atribuir a si mesmo a permissão de plataforma.
- O isolamento multiempresa será obrigatório por RLS. Todas as entidades de negócio carregam organização e, quando aplicável, unidade. Credenciais privilegiadas nunca chegam ao navegador.
- Catálogo central da organização contém serviços. Unidades ativam serviços e sobrescrevem preço e duração. Profissionais são vinculados aos serviços e podem possuir sobrescritas próprias.
- Serviços suportam preço fixo, “a partir de” e “sob avaliação”. Todo serviço agendável exige duração prevista. A reserva guarda snapshot de preço, duração, intervalos e políticas.
- Serviços podem possuir buffer anterior e posterior. Múltiplos serviços são permitidos somente de forma consecutiva com o mesmo profissional no MVP.
- Disponibilidade combina funcionamento da unidade, disponibilidade do profissional, exceções por data, serviços, buffers, reservas, bloqueios temporários, antecedência e grade de início.
- Horário semanal da unidade é herdado inicialmente pelo profissional e pode ser personalizado. Exceções por data prevalecem. Jornadas podem atravessar a meia-noite.
- Grade de início é configurável, com padrão de 15 minutos. Antecedência mínima padrão é uma hora e janela máxima padrão é 60 dias.
- A disponibilidade será uma função central do PostgreSQL, consumida por todos os canais.
- Uma restrição de banco impede sobreposição ativa por profissional. Sobreposição excepcional usa marca explícita, autorização adequada, motivo e auditoria.
- Criação e alteração de reserva ocorrem por comandos transacionais no PostgreSQL. Next.js e Edge Functions chamam os mesmos comandos RPC.
- Página pública permite consulta somente leitura; gravações públicas passam por Supabase Edge Functions com rate limiting, telefone verificado e Cloudflare Turnstile adaptativo.
- Bloqueios temporários de cinco minutos são persistidos no PostgreSQL, participam do conflito enquanto válidos e são limpos posteriormente pelo Cron.
- O fluxo público é serviço primeiro, depois profissional específico ou qualquer disponível. O cliente informa nome e WhatsApp, verifica o telefone na primeira reserva confiável e aceita políticas versionadas.
- Reserva pública é confirmada automaticamente. Se o WhatsApp estiver indisponível, a equipe ainda pode criar reservas manualmente.
- Estados de reserva: agendado, confirmado pelo cliente, em atendimento, concluído, cancelado e falta. “Agendado” já garante o horário; “confirmado” representa a resposta ao lembrete.
- Atraso possui tolerância configurável, padrão de dez minutos. Após o prazo, a reserva é sinalizada, nunca cancelada automaticamente.
- Cancelamento pelo estabelecimento exige motivo, libera o horário, avisa o cliente e oferece remarcação. Quando sinal estiver ativo, dispara reembolso integral.
- Transferência exige novo profissional habilitado e disponível; o cliente pode aceitar ou remarcar sem penalidade.
- Recorrência é criada apenas internamente em frequência semanal, quinzenal ou mensal. Conflitos são apresentados; apenas ocorrências livres podem ser criadas.
- Lista de espera registra serviços, profissional opcional e períodos. Quando surgir vaga, clientes correspondentes recebem link; não existe reserva da vaga e vence quem confirmar primeiro.
- Página de gestão da reserva usa token seguro específico, não revela outras fichas, expira após o atendimento e pode ser invalidado.
- Comandos de texto aceitos: CONFIRMAR, CANCELAR e REMARCAR. Mensagens ambíguas não mudam estado e recebem o link seguro. Cancelamento por texto exige confirmação final.
- Cliente pertence à organização e é deduplicado pelo telefone. Proprietário pode ver histórico consolidado; demais perfis obedecem unidade e relacionamento.
- A ficha contém nome, telefone, histórico, faltas, preferências, observações e alertas simples. Dados clínicos, anamnese e fotos não fazem parte do MVP.
- Importação aceita clientes por CSV com pré-validação e agendamentos futuros por formato separado. Histórico financeiro antigo não é importado.
- Exportação inicial é CSV com filtros por período, unidade, profissional e serviço.
- Avaliação privada pós-atendimento contém nota de um a cinco e comentário opcional. Nota baixa alerta o proprietário. Não há publicação ou ranking.
- WhatsApp inicial é exclusivamente transacional. Campanhas não são permitidas. Consentimento de marketing fica separado para eventual uso futuro.
- UAZAPI, referenciada por https://uazapi.dev/, será o primeiro provedor. O domínio do produto usa uma interface de provedor para permitir Evolution Go no futuro.
- Cada unidade conecta uma instância própria. Somente proprietário conecta ou substitui; gerência apenas consulta status.
- Mensagens padrão: confirmação imediata, lembrete 24 horas antes, lembrete duas horas antes, alterações/cancelamentos imediatos e avaliação pós-atendimento. Tempos são configuráveis.
- Confirmações e alterações urgentes ignoram janela silenciosa. Mensagens não urgentes usam 8h–20h no fuso da unidade por padrão.
- Modelos de mensagem aceitam variáveis seguras e preservam identificação, dados essenciais e link.
- Mensagens gerais recebidas não são armazenadas pelo Meu Beleza. Apenas respostas transacionais reconhecidas são processadas.
- Em desconexão, o proprietário é alertado, mensagens ficam em fila, itens úteis são reenviados e lembretes vencidos são marcados como falha.
- Retentativa de mensagem ocorre até cinco vezes com intervalos crescentes e respeito à utilidade temporal. Erro definitivo vai para fila de falhas e pode ser reenviado manualmente.
- A cobrança de sinal é prevista no domínio como opcional por serviço, valor fixo ou percentual, mas ficará desativada no lançamento até resolver o recebimento direto sem custódia pelo SaaS.
- Política-base de sinal: reembolso antes do limite, retenção após limite ou falta, reembolso integral quando o estabelecimento cancela. Exige validação jurídica antes de ativar.
- AbacatePay será usado para assinatura do SaaS. Cartão atende recorrência mensal/anual; Pix atende anual antecipado. Acesso só muda após webhook confirmado.
- Preços iniciais a validar: Solo R$49,90 por mês para um profissional; Essencial R$89,90 para até cinco; Equipe R$139,90 para até dez. Anual oferece duas mensalidades de desconto.
- Cobrança é por unidade em faixa de profissionais ativos, consolidada em uma assinatura por organização. Proprietário e recepção não contam como profissionais.
- Upgrade exige confirmação antes de ativar profissional acima do limite. Downgrade é solicitado e entra no ciclo seguinte.
- Trial dura 14 dias, sem cartão, com recursos completos. Uma avaliação por CPF/CNPJ e telefone; WhatsApp exige verificação.
- Falha de renovação mantém sete dias de acesso e retentativas. Depois, organização entra em somente leitura, página pública deixa de aceitar reservas e o acesso é restaurado automaticamente após pagamento. Cancelamento por inadimplência começa após 30 dias.
- Cancelamento voluntário vale no fim do período pago, pode ser revertido até lá e segue política de reembolso validada juridicamente.
- Depois do cancelamento, exportação fica disponível por 30 dias, recuperação por 90 dias e posterior exclusão ou anonimização, preservadas obrigações legais.
- Registro financeiro inicial guarda preço previsto/final, desconto, acréscimo, sinal, saldo e pagamentos divididos. Não existe caixa completo.
- Formas de pagamento registráveis: Pix, dinheiro, débito, crédito e outro. Dinheiro é armazenado em centavos inteiros; percentuais usam decimal preciso.
- Comissão padrão pertence ao serviço, com sobrescrita por profissional. Proprietário pode ser “sem comissão”. Comissão nasce apenas no atendimento concluído sobre valor recebido.
- Sinal retido por cancelamento ou falta não gera comissão no MVP.
- Alteração de atendimento concluído é limitada a proprietário/gerência, exige motivo, recalcula efeitos e é auditada.
- Relatórios distinguem faturamento por competência de recebimentos. Sinais retidos têm categoria própria.
- Dashboard inclui agenda, faturamento previsto/recebido, sinais, ocupação, cancelamentos, faltas, comissões, clientes novos e recorrentes.
- Aplicação será web responsiva e instalável; não haverá aplicativo nativo nem operações offline. A agenda já carregada pode ser visualizada temporariamente, sem gravações.
- Profissionais recebem atualização em tempo real, notificação do navegador e resumo por e-mail. Não recebem alertas internos por WhatsApp no MVP.
- Calendário externo será somente leitura. Não haverá sincronização bidirecional no MVP.
- Interface será mobile-first, acessível no nível AA, com visualização ampla da agenda para computador e tablet.
- CSS será vanilla, organizado por CSS Modules e tokens globais em variáveis CSS. Apenas tema claro no MVP.
- Navegadores suportados: versões atual e anterior de Chrome, Edge, Firefox e Safari, incluindo Chrome Android e Safari iOS.
- Frontend e operações web rápidas usarão Next.js com TypeScript, implantado como Cloudflare Worker via OpenNext. Não será usado Cloudflare Pages.
- O Worker Cloudflare serve telas, SSR, sessão e operações rápidas. Não hospeda filas, Cron ou automações.
- Supabase fornece PostgreSQL, Auth, Storage, Realtime, Edge Functions, Queues/PGMQ e Cron/pg_cron.
- UAZAPI e AbacatePay enviam webhooks diretamente a Supabase Edge Functions.
- Webhooks são autenticados, persistidos antes do processamento, enfileirados e tratados idempotentemente. Eventos repetidos ou fora de ordem não duplicam efeitos.
- Alterações do domínio registram eventos em uma outbox na mesma transação. Um dispatcher entrega a fila e marca o evento somente após sucesso.
- Supabase Cron executa a cada minuto, seleciona eventos vencidos em lotes, evita consumo concorrente e os envia à fila. Consumidores revalidam a reserva antes de agir.
- Supabase Realtime notifica mudanças; a interface refaz a consulta autorizada em vez de tratar o evento como fonte final.
- Supabase Storage usa bucket público para identidade da página e buckets privados para comprovantes, exportações e arquivos internos com URLs temporárias.
- Payload bruto de webhook e diagnóstico é retido por 30 dias; depois restam metadados de auditoria. Conversas gerais não são persistidas.
- Trilha de auditoria é imutável para usuários e inclui reserva, bloqueio, preço, pagamento, comissão, permissão, conexão de WhatsApp e suporte administrativo.
- Resend ou Brevo será escolhido antes do piloto. Autenticação usa SMTP personalizado; alertas usam uma interface independente de provedor.
- Sentry registra erros do navegador e Cloudflare Worker; Edge Functions usam logs estruturados; filas, mensagens e webhooks possuem indicadores e alertas. Operações carregam identificador de correlação.
- Supabase terá dois projetos gratuitos separados: dev e prod. Produção terá exportação diária externa criptografada, cópia periódica de Storage, teste mensal de restauração e alerta em 70% dos limites.
- O plano gratuito será reavaliado quando houver clientes pagantes ou aproximação dos limites.
- Git usa branch dev para ambiente de desenvolvimento e main para produção. GitHub Actions executa testes, migrações e deploys.
- Migrações são versionadas e promovidas primeiro a dev e depois a prod. Mudanças manuais em produção são proibidas salvo emergência registrada. Seeds existem apenas em dev.
- Domínios desejados: app.meubeleza.com.br para painel, meubeleza.com.br/<slug> para página pública e status.meubeleza.com.br para status, sujeitos à aquisição e validação de marca.
- O mesmo projeto Next.js contém painel, página pública e área /admin isolada. As autorizações permanecem distintas.
- Suporte humano será por WhatsApp e e-mail em horário comercial, apoiado por central de ajuda e página pública de status.
- A unidade não pode ser desativada com reservas futuras sem transferir, remarcar ou cancelar e notificar. Profissionais seguem regra equivalente.
- Registros com histórico são arquivados/inativados, não apagados. Exclusão definitiva atende dados sem dependência ou processo formal de privacidade.

## Testing Decisions

- Testes devem provar comportamento observável e contratos do produto, não detalhes internos, nomes de funções auxiliares ou estrutura incidental.
- O seam principal é a interface transacional do domínio no Supabase: comandos e consultas usados por todos os canais.
- Testes de banco cobrem RLS, pertencimento a organização/unidade, menor privilégio, isolamento entre organizações e impossibilidade de autoelevação.
- Testes de banco cobrem cálculo de disponibilidade combinando unidade, profissional, exceções, serviços, buffers, grade, antecedência, reservas e holds.
- Testes de concorrência tentam criar duas reservas para o mesmo profissional e intervalo e comprovam que apenas uma vence.
- Testes cobrem a exceção de sobreposição, incluindo permissão, motivo e auditoria.
- Testes cobrem estados e transições da reserva, snapshots históricos, recorrência, transferências, atraso, cancelamento, falta e conclusão.
- Testes cobrem expiração do hold, token seguro do cliente, verificação do telefone e políticas versionadas.
- Testes cobrem catálogo central e sobrescritas por unidade/profissional, inclusive preços variáveis e duração obrigatória.
- Testes cobrem cliente compartilhado dentro da organização e isolado entre organizações.
- Testes cobrem pagamentos divididos, descontos, acréscimos, competência, recebimentos e comissões.
- O segundo seam são contratos HTTP das Supabase Edge Functions. UAZAPI, AbacatePay e e-mail são substituídos por provedores controlados nos testes.
- Testes de contrato usam fixtures representativas e toleram campos novos sem deixar de validar autenticação e campos essenciais.
- Webhooks são testados para assinatura inválida, repetição, chegada fora de ordem, falha parcial e retomada idempotente.
- Filas são testadas para visibility timeout, retentativa, erro definitivo, expiração temporal e reprocessamento manual.
- Outbox é testada para garantir que uma transação do domínio não conclua sem registrar o evento correspondente.
- Cron é testado em torno de limites de horário, fuso IANA, janela silenciosa, reservas canceladas e lembretes já vencidos.
- O terceiro seam é ponta a ponta no aplicativo executado no runtime local do Cloudflare Workers/OpenNext.
- Testes ponta a ponta críticos: onboarding e publicação; reserva pública; reserva manual; confirmação, cancelamento e remarcação; operação diária; conclusão e pagamento; troca de plano; acesso administrativo auditado.
- Cada persona é validada end-to-end: Administrador da Plataforma, proprietário, recepção/gerência, profissional e cliente.
- Testes ponta a ponta verificam também que ações proibidas permanecem invisíveis e são recusadas no servidor.
- Build de produção e preview OpenNext no runtime Workers bloqueiam implantação quando falham.
- Migrações são aplicadas em banco limpo e em snapshot compatível antes de promoção.
- Importação CSV é testada com dados válidos, duplicados, colunas ausentes, formatos brasileiros e processamento parcial seguro.
- Exportação CSV é testada para filtros, encoding e isolamento de organização.
- Acessibilidade automatizada e fluxos por teclado integram os testes de interface; revisão manual complementa os casos principais.
- Responsividade é validada em larguras móveis, tablet e desktop nos navegadores oficialmente suportados.
- Restauração de backup externo é exercitada mensalmente em ambiente isolado.
- Não existe prior art de testes no repositório, pois o projeto é greenfield. As suítes desta especificação estabelecerão os padrões iniciais.
- Toda falha de teste, migração, build ou preview bloqueia promoção de dev para main.

## Out of Scope

- Marketplace público para descoberta de estabelecimentos.
- Aplicativos nativos para Android ou iOS.
- Operações de escrita offline.
- Tema escuro.
- Atendimento em domicílio, área de cobertura, deslocamento e taxas de viagem.
- Gestão de recursos físicos como salas, cadeiras, macas e equipamentos.
- Atendimento simultâneo de vários clientes pelo mesmo profissional.
- Múltiplos profissionais na mesma reserva.
- Caixa completo, despesas, conciliação bancária, estoque, venda de produtos e emissão fiscal.
- Pacotes de serviços, créditos, clube de assinatura de clientes e programa de fidelidade.
- Prontuário, anamnese, dados clínicos e fotos de procedimentos.
- Marketing, campanhas, mensagens em massa e reativação promocional.
- Caixa de entrada compartilhada, chatbot, IA de atendimento e armazenamento de conversas gerais.
- API oficial da Meta no MVP.
- SMS como contingência de WhatsApp.
- Sincronização bidirecional com Google Calendar ou outros calendários.
- Domínio personalizado por estabelecimento e white-label.
- Avaliações públicas, ranking e reputação em marketplace.
- PDF formatado e relatórios contábeis.
- Importação de histórico financeiro ou atendimentos antigos.
- Autenticação em dois fatores.
- Internacionalização, moedas estrangeiras e operação fora do Brasil.
- Cobrança ativa de sinal antes da resolução técnica do recebimento direto.
- Compartilhamento de agenda do profissional entre organizações distintas.
- Suporte 24 horas.

## Further Notes

- Pendência técnica: definir provedor e arquitetura de cobrança do sinal com recebimento direto pelo estabelecimento, sem custódia pelo Meu Beleza. O domínio deve ficar preparado, mas a função permanece desativada.
- Pendência técnica: escolher Resend ou Brevo antes do piloto, preservando uma interface independente de provedor.
- Pendência comercial/jurídica: verificar disponibilidade e registro da marca Meu Beleza e aquisição de meubeleza.com.br.
- Pendência jurídica: validar política de sinal, cancelamento, retenção, reembolso, termos, privacidade e prazos de exclusão.
- Pendência operacional: confirmar por escrito com a UAZAPI o uso multiestabelecimento dentro do SaaS e condições comerciais aplicáveis.
- UAZAPI é o primeiro provedor; Evolution Go permanece opção futura e deve caber no mesmo contrato interno.
- O uso de integração não oficial com WhatsApp implica risco de restrição ou banimento. Consentimento, volume transacional e monitoramento de conexão devem ser tratados como riscos explícitos.
- Preços são hipóteses iniciais, não evidência de disposição a pagar.
- Piloto fechado: três a cinco operações reais, incluindo ao menos barbearia, salão e manicure ou designer de sobrancelhas; até cinco profissionais; uso diário de WhatsApp; reunião semanal de feedback.
- O piloto pode começar quando agenda, reserva pública e WhatsApp estiverem funcionais, mesmo antes da conclusão do MVP amplo.
- Lançamento comercial exige todo o escopo desta especificação.
- Critérios iniciais de piloto após quatro semanas: 70% dos agendamentos registrados no sistema; 25% pelo link público; nenhum conflito grave; mensagens confiáveis; economia relatada de três horas semanais; três participantes dispostos a pagar.
- Projetos Supabase gratuitos não oferecem a proteção esperada de uma produção madura. Backups externos e limites de upgrade são condições de operação, não melhorias opcionais.
- A configuração do rastreador local ainda referencia o nome antigo Resp94/saas; o repositório canônico no GitHub é Resp94/MeuBeleza.
