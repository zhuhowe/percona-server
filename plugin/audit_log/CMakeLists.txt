# Copyright (c) 2014 Percona LLC and/or its affiliates. All rights reserved.
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA

MYSQL_ADD_PLUGIN(audit_log audit_log.cc file_logger.cc buffer.cc audit_file.cc
 audit_syslog.cc filter.cc
 MODULE_ONLY MODULE_OUTPUT_NAME "audit_log")

IF(UNIX)
  IF(INSTALL_MYSQLTESTDIR)
    INSTALL(DIRECTORY tests/mtr/ DESTINATION ${INSTALL_MYSQLTESTDIR}/suite/audit_log COMPONENT Test)
  ENDIF()
ENDIF()
