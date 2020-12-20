-- phpMyAdmin SQL Dump
-- version 5.0.4
-- https://www.phpmyadmin.net/
--
-- Servidor: 127.0.0.1
-- Tiempo de generación: 19-12-2020 a las 17:57:10
-- Versión del servidor: 10.4.17-MariaDB
-- Versión de PHP: 8.0.0

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Base de datos: `covid_db`
--

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `health_facilities`
--

CREATE TABLE `health_facilities` (
  `facility_id` int(11) NOT NULL,
  `facility_region` enum('RS_ALT_PIRINEU_ARAN','RS_LLEIDA','RS_CAMP_TARRAGONA','RS_TERRES_EBRE','RS_CATALUNYA_CENTRAL','RS_GIRONA','RS_BARCELONA') NOT NULL,
  `facility_name` varchar(50) NOT NULL,
  `facility_address` varchar(100) NOT NULL,
  `facility_zipcode` int(5) NOT NULL,
  `facility_city` varchar(50) NOT NULL,
  `facility_responsable_id` int(11) NOT NULL,
  `facility_contact_phone` varchar(9) NOT NULL,
  `facility_contact_email` varchar(50) NOT NULL,
  `facility_patient_capacity` int(4) NOT NULL,
  `facility_total_respirators` int(3) NOT NULL,
  `facility_respirators_availability` int(3) NOT NULL,
  `IS_facility_icu` tinyint(1) NOT NULL,
  `facility_total_icu_rooms` int(2) NOT NULL,
  `facility_icu_rooms_availability` int(2) NOT NULL,
  `IS_facility_operating_room` tinyint(1) NOT NULL,
  `facility_total_operating_room` int(2) NOT NULL,
  `facility_operating_room_availability` int(2) NOT NULL,
  `IS_covid_room` tinyint(1) NOT NULL,
  `facility_total_room` int(3) NOT NULL,
  `facility_room_availability` int(3) NOT NULL,
  `facility_staff` int(4) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `health_facilities`
--

INSERT INTO `health_facilities` (`facility_id`, `facility_region`, `facility_name`, `facility_address`, `facility_zipcode`, `facility_city`, `facility_responsable_id`, `facility_contact_phone`, `facility_contact_email`, `facility_patient_capacity`, `facility_total_respirators`, `facility_respirators_availability`, `IS_facility_icu`, `facility_total_icu_rooms`, `facility_icu_rooms_availability`, `IS_facility_operating_room`, `facility_total_operating_room`, `facility_operating_room_availability`, `IS_covid_room`, `facility_total_room`, `facility_room_availability`, `facility_staff`) VALUES
(1, 'RS_ALT_PIRINEU_ARAN', 'HOSPITAL DE PUIGCERDÀ', 'PJ. DE JOAN PRUDIEU; LA CEU D\'URGELL', 25700, 'PUIGCERDÀ', 1, '973350050', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(2, 'RS_LLEIDA', 'HOSPITAL DE SANTA MARIA', 'AV. ALCALDE ROVIRA ROURA 94', 25198, 'SEGRIÀ', 1, '973727222', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(3, 'RS_CAMP_TARRAGONA', 'HOSPITAL SANT JOAN DE REUS', 'JOSEP LAPORTE, S/N ', 43206, 'BAIX CAMP', 1, '977337303', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(4, 'RS_TERRES_EBRE', 'HOSPITAL COMARCAL MÓRA D\'EBRE', 'BENET I MESSENGUER ', 43740, 'RIBERA D\'EBRE', 1, '977401674', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(5, 'RS_CATALUNYA_CENTRAL', 'HOSPITAL SANT JOAN DE DEU', 'AV. MANCOMUNITATS COMARCALS 1', 8760, 'MARTORELL', 1, '937742020', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(6, 'RS_GIRONA', 'HOSPITAL DE PALAMÓS', 'HOSPITAL, 33', 17230, 'PALAMOS', 1, '972600160', 'NO', 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0),
(7, 'RS_BARCELONA', 'HOSPITAL VALL D\'HEBRON', 'PASEIG DE LA VALL D\'HEBRON, 119-129', 8035, 'BARCELONA', 1, '934893000', 'www.vallhebron.com/ca/contacta', 500, 100, 25, 1, 400, 100, 1, 20, 15, 1, 4, 1, 250);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `patient_list`
--

CREATE TABLE `patient_list` (
  `patient_id` int(11) NOT NULL,
  `patient_type` int(11) NOT NULL,
  `patient_location` varchar(20) NOT NULL,
  `patient_last_contacted` datetime NOT NULL,
  `patient_symptoms1` varchar(100) DEFAULT NULL,
  `patient_symptoms2` varchar(100) DEFAULT NULL,
  `patient_symptoms3` varchar(100) DEFAULT NULL,
  `patient_symptoms4` varchar(100) DEFAULT NULL,
  `patient_symptoms5` varchar(100) DEFAULT NULL,
  `patient_sypmtoms_observations` text NOT NULL,
  `patient_medication1` varchar(100) DEFAULT NULL,
  `patient_medication2` varchar(100) DEFAULT NULL,
  `patient_medication3` varchar(100) DEFAULT NULL,
  `patient_medication4` varchar(100) DEFAULT NULL,
  `patient_medication5` varchar(100) DEFAULT NULL,
  `patient_medication_observations` text NOT NULL,
  `patient_facility_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `patient_list`
--

INSERT INTO `patient_list` (`patient_id`, `patient_type`, `patient_location`, `patient_last_contacted`, `patient_symptoms1`, `patient_symptoms2`, `patient_symptoms3`, `patient_symptoms4`, `patient_symptoms5`, `patient_sypmtoms_observations`, `patient_medication1`, `patient_medication2`, `patient_medication3`, `patient_medication4`, `patient_medication5`, `patient_medication_observations`, `patient_facility_id`) VALUES
(3, 5, 'A1', '2020-12-15 02:59:39', 'TOS SECA', NULL, NULL, NULL, NULL, 'PROBABILIDAD ALTA DE COVID', 'BISOLVON', NULL, NULL, NULL, NULL, 'DOSIS BASTANTE ALTA PARA LOS SINTOMAS ', 7),
(4, 5, 'B2', '2020-12-09 16:37:39', 'FIEBRE', NULL, NULL, NULL, NULL, '', 'PARACETAMOL', NULL, NULL, NULL, NULL, 'SINTOMAS RELACIONADOS CON EL COVID', 7),
(5, 5, 'A3', '2020-12-02 15:03:21', 'CANSANCIO', NULL, NULL, NULL, NULL, '', 'REPOSO', NULL, NULL, NULL, NULL, '', 7);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `patient_related_list`
--

CREATE TABLE `patient_related_list` (
  `contact_id` int(11) NOT NULL,
  `contact_patient_related_id` int(11) NOT NULL,
  `contact_last_contacted` datetime NOT NULL,
  `IS_have_sympthoms` tinyint(1) NOT NULL,
  `contact_sympthoms1` varchar(100) DEFAULT NULL,
  `contact_sympthoms2` varchar(100) DEFAULT NULL,
  `contact_sympthoms3` varchar(100) DEFAULT NULL,
  `contact_sympthoms4` varchar(100) DEFAULT NULL,
  `contact_sympthoms5` varchar(100) DEFAULT NULL,
  `contact_sympthoms_observations` text NOT NULL,
  `IS_test_declared` tinyint(1) NOT NULL,
  `contact_test_type` enum('PCR','IgM','IgG','') NOT NULL,
  `contact_test_result` tinyint(1) NOT NULL,
  `patient_related_contacted` tinyint(1) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `patient_related_list`
--

INSERT INTO `patient_related_list` (`contact_id`, `contact_patient_related_id`, `contact_last_contacted`, `IS_have_sympthoms`, `contact_sympthoms1`, `contact_sympthoms2`, `contact_sympthoms3`, `contact_sympthoms4`, `contact_sympthoms5`, `contact_sympthoms_observations`, `IS_test_declared`, `contact_test_type`, `contact_test_result`, `patient_related_contacted`) VALUES
(6, 3, '2020-12-19 14:14:53', 1, 'TOS SECA', 'DOLOR DE GARGANTA', NULL, NULL, NULL, 'ESTA TIENE.', 1, 'PCR', 1, 1),
(7, 3, '2020-12-13 07:28:17', 1, 'PERDIDA DEL SENTIDO DEL OLFATO', 'PERDIDA DEL GUSTO', 'DOLOR DE CABEZA', NULL, NULL, 'DEBERIA HACERSE UNA PCR.', 0, '', 0, 0),
(8, 4, '2020-12-09 17:30:10', 1, 'MOLESTIA Y DOLORES ', NULL, NULL, NULL, NULL, 'RECOMENDAMOS UNA TERAPIA ANTIINFLAMATORIA.', 1, 'PCR', 0, 1),
(9, 5, '2020-12-06 08:33:32', 1, 'DOLOR EN EL PECHO JUNTO CON SENSACION DE PRESION', NULL, NULL, NULL, NULL, '', 1, 'IgM', 1, 0),
(10, 4, '2020-12-13 17:01:56', 1, 'INCAPACIDAD PARA HABLAR', 'INCAPACIDAD PARA MOVERSE', NULL, NULL, NULL, 'ALTA RECOMENDACION DE REALIZAR UN TRATAMIENTO BASTANTE ESPECIAL. (POSIBILIDAD DE FUNERAL ALTA)', 0, '', 0, 0),
(11, 5, '2020-12-09 09:04:24', 1, 'DIFICULTAD PARA RESPIRAR', 'SENSACION DE FALTA DE AIRE', NULL, NULL, NULL, 'RECOMAENDAMOS DEXAMETASONA Y EVITAR ESFUERZOS FISICOS', 1, 'IgG', 1, 1);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `user`
--

CREATE TABLE `user` (
  `user_id` int(11) NOT NULL,
  `user_name` varchar(20) NOT NULL,
  `user_surname1` varchar(20) NOT NULL,
  `user_surname2` varchar(20) DEFAULT NULL,
  `user_idcode` varchar(11) NOT NULL,
  `user_contact_address` varchar(100) NOT NULL,
  `user_contact_zipcode` int(5) NOT NULL,
  `user_contact_phone` varchar(9) NOT NULL,
  `user_contact_email` varchar(50) NOT NULL,
  `user_type` int(11) NOT NULL,
  `user_status` int(11) NOT NULL,
  `user_health_facilities_primary` int(11) NOT NULL,
  `user_health_facilities_hospital` int(11) NOT NULL,
  `user_language` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `user`
--

INSERT INTO `user` (`user_id`, `user_name`, `user_surname1`, `user_surname2`, `user_idcode`, `user_contact_address`, `user_contact_zipcode`, `user_contact_phone`, `user_contact_email`, `user_type`, `user_status`, `user_health_facilities_primary`, `user_health_facilities_hospital`, `user_language`) VALUES
(1, 'NICOLAS', 'RAMOS', 'MIGNONE', '47907791X', 'SANT JOAN DESPI; TORREBLANCA 18 1º2ª', 8970, '638608927', 'NICORAMOS.BCN@GMAIL.COM', 1, 1, 1, 1, 'ESP'),
(2, 'DANIEL', 'MARIN', 'SERRA', '18756892D', 'SANT BOI: CARRER 2 1º1ª', 8830, '669806877', 'DMARIN@GMAIL.COM', 2, 2, 1, 1, 'CAT'),
(3, 'MARIA', 'SOL', 'DE PRADO', '47546791W', 'CARRER DE LA PAU 34 4º4ª', 8950, '653214657', 'MERYSOL67@GMAIL.COM', 5, 1, 1, 1, 'ESP'),
(4, 'IVAN', 'LOPEZ', 'GARCIA', '18764792J', 'CARRER MARQUES DE MULHACEN 2; 1º2ª', 8034, '670256832', 'IVANSITOLOPES@GMAIL.COM', 5, 1, 1, 1, 'ESP'),
(5, 'ISMAEL', 'POLO', 'FERNANDEZ', '14564728S', 'CARRER DE TORREBLANCA 18; 4º 1ª', 8970, '648725641', 'POLITOPOLO@GMAIL.COM', 5, 1, 1, 1, 'CAT'),
(6, 'NAIARA', 'BARRER', 'SIERRA', '62487556D', 'CARRER PAU CLARÍS 3 1º3ª', 8010, '668445719', 'BARRERRNS@GMAIL.COM', 5, 1, 1, 1, 'CAT'),
(7, 'BLANCA', 'PALOMARES', NULL, '44578169G', 'SANT MARTIN PROVENSALS 23, 2º 2ª', 8020, '646876594', 'BLANCACOMOLAMAR@GMAIL.COM', 5, 1, 1, 1, 'CAT'),
(8, 'VLADIMIR', 'ROSMANINOV', NULL, '64887751R', 'CARRER DE BISCAIA, 2 1º 3ª', 8027, '654654456', 'ALBERTOCP@GMAIL.COM', 5, 1, 1, 1, 'RU'),
(9, 'GLORIA', 'CANOVAS', 'CANOVAS', '34897784D', 'CALLE BALMES 58, 2º 2ª', 8007, '644875111', 'GLORIABENDITA@GMAIL.COM', 5, 1, 1, 1, 'ESP'),
(10, 'LUIS', 'MIGUEL', NULL, '65478995S', 'CARRER DE VALENCIA, 441, 3º 1ª', 8013, '684751157', 'LUISMIGUELON@GMAIL.COM', 5, 1, 1, 1, 'ESP'),
(11, 'JAUME', 'DIEGUEZ', NULL, '47654791F', 'CARRER DE LA PAU; 4 7º 1ª', 8002, '664789514', 'JAUMEDIE@GMAIL.COM', 5, 1, 1, 1, 'CAT');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `user_status`
--

CREATE TABLE `user_status` (
  `user_status_id` int(11) NOT NULL,
  `user_status_value` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `user_status`
--

INSERT INTO `user_status` (`user_status_id`, `user_status_value`) VALUES
(1, 'ACTIVE'),
(2, 'BLOCKED');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `user_type`
--

CREATE TABLE `user_type` (
  `user_type_id` int(11) NOT NULL,
  `user_type_value` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- Volcado de datos para la tabla `user_type`
--

INSERT INTO `user_type` (`user_type_id`, `user_type_value`) VALUES
(1, 'ADMIN'),
(2, 'FACULTATIVE'),
(5, 'PATIENT');

--
-- Índices para tablas volcadas
--

--
-- Indices de la tabla `health_facilities`
--
ALTER TABLE `health_facilities`
  ADD PRIMARY KEY (`facility_id`),
  ADD KEY `FK_FACILITY_RESPONSABLE_ID` (`facility_responsable_id`);

--
-- Indices de la tabla `patient_list`
--
ALTER TABLE `patient_list`
  ADD PRIMARY KEY (`patient_id`),
  ADD KEY `FK_PATIENT_TYPE` (`patient_type`),
  ADD KEY `FK_FACILITY_ID` (`patient_facility_id`);

--
-- Indices de la tabla `patient_related_list`
--
ALTER TABLE `patient_related_list`
  ADD PRIMARY KEY (`contact_id`),
  ADD KEY `FK contact_patient_related_id` (`contact_patient_related_id`);

--
-- Indices de la tabla `user`
--
ALTER TABLE `user`
  ADD PRIMARY KEY (`user_id`),
  ADD KEY `FK_USER_STATUS_ID` (`user_status`),
  ADD KEY `FK_USER_TYPE_ID` (`user_type`);

--
-- Indices de la tabla `user_status`
--
ALTER TABLE `user_status`
  ADD PRIMARY KEY (`user_status_id`);

--
-- Indices de la tabla `user_type`
--
ALTER TABLE `user_type`
  ADD PRIMARY KEY (`user_type_id`);

--
-- AUTO_INCREMENT de las tablas volcadas
--

--
-- AUTO_INCREMENT de la tabla `health_facilities`
--
ALTER TABLE `health_facilities`
  MODIFY `facility_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=8;

--
-- AUTO_INCREMENT de la tabla `patient_list`
--
ALTER TABLE `patient_list`
  MODIFY `patient_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=11;

--
-- AUTO_INCREMENT de la tabla `patient_related_list`
--
ALTER TABLE `patient_related_list`
  MODIFY `contact_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT de la tabla `user`
--
ALTER TABLE `user`
  MODIFY `user_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT de la tabla `user_status`
--
ALTER TABLE `user_status`
  MODIFY `user_status_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT de la tabla `user_type`
--
ALTER TABLE `user_type`
  MODIFY `user_type_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=7;

--
-- Restricciones para tablas volcadas
--

--
-- Filtros para la tabla `health_facilities`
--
ALTER TABLE `health_facilities`
  ADD CONSTRAINT `FK_FACILITY_RESPONSABLE_ID` FOREIGN KEY (`facility_responsable_id`) REFERENCES `user` (`user_id`);

--
-- Filtros para la tabla `patient_list`
--
ALTER TABLE `patient_list`
  ADD CONSTRAINT `FK_FACILITY_ID` FOREIGN KEY (`patient_facility_id`) REFERENCES `health_facilities` (`facility_id`),
  ADD CONSTRAINT `FK_PATIENT_ID` FOREIGN KEY (`patient_id`) REFERENCES `user` (`user_id`),
  ADD CONSTRAINT `FK_PATIENT_TYPE` FOREIGN KEY (`patient_type`) REFERENCES `user_type` (`user_type_id`);

--
-- Filtros para la tabla `patient_related_list`
--
ALTER TABLE `patient_related_list`
  ADD CONSTRAINT `FK contact_id` FOREIGN KEY (`contact_id`) REFERENCES `user` (`user_id`),
  ADD CONSTRAINT `FK contact_patient_related_id` FOREIGN KEY (`contact_patient_related_id`) REFERENCES `user` (`user_id`);

--
-- Filtros para la tabla `user`
--
ALTER TABLE `user`
  ADD CONSTRAINT `FK_USER_STATUS_ID` FOREIGN KEY (`user_status`) REFERENCES `user_status` (`user_status_id`),
  ADD CONSTRAINT `FK_USER_TYPE_ID` FOREIGN KEY (`user_type`) REFERENCES `user_type` (`user_type_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
