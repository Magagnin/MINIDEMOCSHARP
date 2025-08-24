using System; // #biblioteca principal do C#

class Program
{
    static void Main(string[] args)
    {
        // título da janela do console 
        Console.Title = "Jogo do Número Secreto";

        // cor do título em azul 
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("=== 🎲 Mini Demo: Jogo do Número Secreto ===\n");
        Console.ResetColor();

        // biblioteca da linguagem que serve para gerar números aleatórios
        Random random = new Random();

        // // Sorteia número secreto entre 1 e 10
        int numeroSecreto = random.Next(1, 11); // 1 a 10
        int tentativas = 0; // contador de tentativas 
        int chute = -1; // guarda o palpite 

        // explica como o jogo funciona 
        Console.WriteLine("Tente adivinhar o número (entre 1 e 10).\n");

        // enquanto não acertar o número secreto, repete o loop
        while (chute != numeroSecreto)
        {
            Console.Write("Digite seu palpite: "); // pede o palpite do usuário
            string? input = Console.ReadLine();

            // tenta converter a entrada para inteiro
            if (int.TryParse(input, out chute))
            {
                tentativas++; // incrementa o contador de tentativas
                if (chute < numeroSecreto)
                {
                     // Se o palpite for menor que o número secreto
                    Console.ForegroundColor = ConsoleColor.Yellow;
                    Console.WriteLine("➡ O número secreto é MAIOR!\n");
                }
                else if (chute > numeroSecreto)
                {
                     // Se o palpite for maior que o número secreto
                    Console.ForegroundColor = ConsoleColor.Yellow;
                    Console.WriteLine("⬅ O número secreto é MENOR!\n");
                }
                else
                {
                    // Se o palpite estiver correto
                    Console.ForegroundColor = ConsoleColor.Green;
                    Console.WriteLine($"✅ Acertou! O número secreto era {numeroSecreto}.");
                    Console.WriteLine($"Tentativas: {tentativas}");
                    Console.ResetColor();
                }
            }
            else
            {
                // Se a entrada não for um número válido
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine("⚠ Entrada inválida! Digite um número inteiro.\n");
                Console.ResetColor();
            }
        }
        // mensagem de despedida
        Console.WriteLine("\nObrigado por jogar! 🚀");
    }
}
