# controle_veiculo_16_04_2021



CREATE TABLE empresa (
                id INT NOT NULL,
                nome VARCHAR(255) NOT NULL,
                logo VARCHAR(255),
                PRIMARY KEY (id)
);


CREATE TABLE origem_destino (
                id INT NOT NULL,
                descricao VARCHAR(255) NOT NULL,
                empresa_id INT NOT NULL,
                PRIMARY KEY (id)
);


CREATE TABLE usuario (
                id INT NOT NULL,
                nome VARCHAR(255) NOT NULL,
                email VARCHAR(255) NOT NULL,
                senha VARCHAR(255) NOT NULL,
                ativo BOOLEAN NOT NULL,
                empresa_id INT NOT NULL,
                PRIMARY KEY (id)
);


CREATE TABLE veiculo (
                id INT NOT NULL,
                nome VARCHAR(255) NOT NULL,
                placa VARCHAR(255) NOT NULL,
                empresa_id INT NOT NULL,
                PRIMARY KEY (id)
);


CREATE TABLE controle_veiculo (
                id INT NOT NULL,
                data DATE NOT NULL,
                hora_saida TIME NOT NULL,
                km_saida INT NOT NULL,
                origem_id INT NOT NULL,
                destino_id INT NOT NULL,
                hora_chegada TIME NOT NULL,
                km_chegada INT NOT NULL,
                usuario_id INT NOT NULL,
                veiculo_id INT NOT NULL,
                empresa_id INT NOT NULL,
                origem_destino_id INT NOT NULL,
                PRIMARY KEY (id)
);


ALTER TABLE veiculo ADD CONSTRAINT empresa_veiculo_fk
FOREIGN KEY (empresa_id)
REFERENCES empresa (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE usuario ADD CONSTRAINT empresa_usuario_fk
FOREIGN KEY (empresa_id)
REFERENCES empresa (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE origem_destino ADD CONSTRAINT empresa_origem_destino_fk
FOREIGN KEY (empresa_id)
REFERENCES empresa (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE controle_veiculo ADD CONSTRAINT empresa_controle_veiculo_fk
FOREIGN KEY (empresa_id)
REFERENCES empresa (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE controle_veiculo ADD CONSTRAINT origem_destino_controle_veiculo_fk
FOREIGN KEY (origem_id)
REFERENCES origem_destino (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE controle_veiculo ADD CONSTRAINT origem_destino_controle_veiculo_fk1
FOREIGN KEY (destino_id)
REFERENCES origem_destino (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE controle_veiculo ADD CONSTRAINT usuario_controle_veiculo_fk
FOREIGN KEY (usuario_id)
REFERENCES usuario (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;

ALTER TABLE controle_veiculo ADD CONSTRAINT veiculo_controle_veiculo_fk
FOREIGN KEY (veiculo_id)
REFERENCES veiculo (id)
ON DELETE NO ACTION
ON UPDATE NO ACTION;
