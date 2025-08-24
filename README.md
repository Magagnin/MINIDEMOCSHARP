[Program.cs](https://github.com/user-attachments/files/21959168/Program.cs)
using System; // Importa a biblioteca principal do C# (entrada/saída, Random etc.)

class Program
{
    static void Main(string[] args)
    {
        // Configura título da janela do console
        Console.Title = "Jogo do Número Secreto";

        // Mensagem inicial em azul
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("=== 🎲 Mini Demo: Jogo do Número Secreto ===\n");
        Console.ResetColor();

        // Cria gerador de números aleatórios
        Random random = new Random();

        // Sorteia número secreto entre 1 e 10
        int numeroSecreto = random.Next(1, 11);

        int tentativas = 0; // Conta quantas tentativas foram feitas
        int chute = -1;     // Guarda o palpite do jogador

        // Explica ao usuário como jogar
        Console.WriteLine("Tente adivinhar o número (entre 1 e 10).\n");

        // Enquanto não acertar, continua no loop
        while (chute != numeroSecreto)
        {
            Console.Write("Digite seu palpite: ");
            string? input = Console.ReadLine(); // Lê o que o usuário digitou

            // Tenta converter para número inteiro (seguro, evita erro se digitar texto)
            if (int.TryParse(input, out chute))
            {
                tentativas++; // Conta mais uma tentativa

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
                    // Acertou!
                    Console.ForegroundColor = ConsoleColor.Green;
                    Console.WriteLine($"✅ Acertou! O número secreto era {numeroSecreto}.");
                    Console.WriteLine($"Tentativas: {tentativas}");
                    Console.ResetColor();
                }
            }
            else
            {
                // Caso o usuário não digite um número válido
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine("⚠ Entrada inválida! Digite um número inteiro.\n");
                Console.ResetColor();
            }
        }

        // Mensagem final
        Console.WriteLine("\nObrigado por jogar! 🚀");
    }
}
