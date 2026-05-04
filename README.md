CREATE DATABASE IF NOT EXISTS techforge;
USE techforge;

CREATE TABLE IF NOT EXISTS projetos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    linguagem VARCHAR(50) NOT NULL,
    orcamento DECIMAL(10,2),
    data_inicio DATE
);

INSERT INTO projetos (nome, linguagem, orcamento, data_inicio) VALUES 
('Sistema Financeiro', 'C++', 150000.00, '2024-01-15'),
('Plataforma Web', 'Python', 95000.50, '2024-03-10'),
('Banco de Dados Corporativo', 'SQL', 200000.00, '2023-11-01'),
('Motor de Jogos', 'C++', 300000.75, '2024-05-20'),
('Analise de Dados', 'Python', 120000.00, '2024-02-05');

SELECT * FROM projetos;

SELECT nome, orcamento
FROM projetos
WHERE linguagem = 'C++';

UPDATE projetos
SET orcamento = 18000.00
WHERE id = 1;

DELETE FROM projetos
WHERE id = 3;

SELECT 
    COUNT(*) AS total_projetos,
    AVG(orcamento) AS media_orcamento
FROM projetos;

SELECT 
    linguagem,
    COUNT(*) AS total_projetos
FROM projetos
GROUP BY linguagem;

SELECT 
    linguagem,
    SUM(orcamento) AS total_orcamento
FROM projetos
GROUP BY linguagem
HAVING SUM(orcamento) > 20000.00;

SELECT nome, orcamento
FROM projetos
    ORDER BY orcamento DESC